add_fpga_target(
  NAME ram_test
  BOARD basys3
  INPUT_IO_FILE basys3.pcf
  SOURCES uart.v uart_rx.v uart_tx.v top.v baudgen.v ram_test.v lfsr.v error_output_logic.v
  )

get_target_property_required(DEVICE basys3 DEVICE)
get_target_property_required(ARCH ${DEVICE} ARCH)
get_target_property_required(SYNTH_V ram_test SYNTH_V)

add_autosim(
    NAME ram_test_autosim_synth
    TOP top
    ARCH ${ARCH}
    SOURCES ${SYNTH_V}
    CYCLES 3000
    )
