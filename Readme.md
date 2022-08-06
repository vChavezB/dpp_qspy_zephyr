# DPP QPCPP with QSPY for Zephyr

Example integration of QSpy in the DPP example of the [QPCPP framework](https://github.com/QuantumLeaps/qpcpp) for the  Zephyr port.

This repository contains an example integration of how to integrate QSPy in to the zephyr port.This example uses Zephyr's [console UART](https://github.com/vChavezB/dpp_qspy_zephyr/blob/main/src/bsp.cpp#L226). 

## Dependencies

This example uses an external [custom Zephyr module](https://github.com/vChavezB/qpcpp_zephyr) to facilitate the integration of QPCPP as a Zephyr Library module. 


## Installation

```bash
git clone https://github.com/vChavezB/dpp_qspy_zephyr --recurse-submodules
```
QSPY is enabled by default in `prj.conf` as `CONFIG_QSPY=y`. This is passed to the [qpcpp_zephyr module](https://github.com/vChavezB/qpcpp_zephyr) and automatically selects the correct files to build Qspy for your Zephyr application.

## Build 

### NRF52 example

```bash
git clone https://github.com/vChavezB/dpp_qspy_zephyr --recurse-submodules
mkdir west_workspace
cd west_workspace
west init -m https://github.com/nrfconnect/sdk-nrf/
west update --narrow -o=--depth=1
west build ../dpp_qspy_zephyr --board nrf52833dk_nrf52833
```

#### Test

Run qspy


```
qspy -c YOUR_COMPORT
```

##### Output
```
########## Trg-RST  QP-Ver=701,Build=220806_131317
           Obj-Dict 0x20003154->QS_RX
           Obj-Dict 0x20000680->AO_Table
           Obj-Dict 0x20000180->AO_Philo[0]
           Obj-Dict 0x20000280->AO_Philo[1]
           Obj-Dict 0x20000380->AO_Philo[2]
           Obj-Dict 0x20000480->AO_Philo[3]
           Obj-Dict 0x20000580->AO_Philo[4]
           Obj-Dict 0x0000A52C->timerID
           Usr-Dict 00000100->PHILO_STAT
           Usr-Dict 00000101->PAUSED_STAT
           Usr-Dict 00000102->COMMAND_STAT
           Usr-Dict 00000103->CONTEXT_SW
           Obj-Dict 0x20003054->EvtPool1
           Obj-Dict 0x20000180->Philo::inst[0]
           Obj-Dict 0x2000026C->Philo::inst[0].m_timeEvt
           Obj-Dict 0x20000280->Philo::inst[1]
           Obj-Dict 0x2000036C->Philo::inst[1].m_timeEvt
           Obj-Dict 0x20000380->Philo::inst[2]
           Obj-Dict 0x2000046C->Philo::inst[2].m_timeEvt
           Obj-Dict 0x20000480->Philo::inst[3]
           Obj-Dict 0x2000056C->Philo::inst[3].m_timeEvt
           Obj-Dict 0x20000580->Philo::inst[4]
           Obj-Dict 0x2000066C->Philo::inst[4].m_timeEvt
           Fun-Dict 0x00008929->Philo::initial
           Fun-Dict 0x0000890F->Philo::thinking
           Fun-Dict 0x00008917->Philo::hungry
           Fun-Dict 0x0000891F->Philo::eating
           Sig-Dict 00000004,Obj=0x00000000->TIMEOUT_SIG
0000000327 AO-Subsc Obj=Philo::inst[0],Sig=00000005,Obj=0x20000180
0000000327 AO-Subsc Obj=Philo::inst[0],Sig=00000009,Obj=0x20000180
===RTC===> St-Init  Obj=Philo::inst[0],State=0x00009B1B->Philo::thinking
===RTC===> St-Entry Obj=Philo::inst[0],State=Philo::thinking
0000000328 Init===> Obj=Philo::inst[0],State=Philo::thinking
0000000334 AO-Subsc Obj=Philo::inst[1],Sig=00000005,Obj=0x20000280
0000000334 AO-Subsc Obj=Philo::inst[1],Sig=00000009,Obj=0x20000280
===RTC===> St-Init  Obj=Philo::inst[1],State=0x00009B1B->Philo::thinking
===RTC===> St-Entry Obj=Philo::inst[1],State=Philo::thinking
0000000334 Init===> Obj=Philo::inst[1],State=Philo::thinking
0000000340 AO-Subsc Obj=Philo::inst[2],Sig=00000005,Obj=0x20000380
0000000340 AO-Subsc Obj=Philo::inst[2],Sig=00000009,Obj=0x20000380
===RTC===> St-Init  Obj=Philo::inst[2],State=0x00009B1B->Philo::thinking
===RTC===> St-Entry Obj=Philo::inst[2],State=Philo::thinking
0000000340 Init===> Obj=Philo::inst[2],State=Philo::thinking
0000000346 AO-Subsc Obj=Philo::inst[3],Sig=00000005,Obj=0x20000480
0000000346 AO-Subsc Obj=Philo::inst[3],Sig=00000009,Obj=0x20000480
===RTC===> St-Init  Obj=Philo::inst[3],State=0x00009B1B->Philo::thinking
===RTC===> St-Entry Obj=Philo::inst[3],State=Philo::thinking
0000000346 Init===> Obj=Philo::inst[3],State=Philo::thinking
0000000352 AO-Subsc Obj=Philo::inst[4],Sig=00000005,Obj=0x20000580
0000000352 AO-Subsc Obj=Philo::inst[4],Sig=00000009,Obj=0x20000580
===RTC===> St-Init  Obj=Philo::inst[4],State=0x00009B1B->Philo::thinking
===RTC===> St-Entry Obj=Philo::inst[4],State=Philo::thinking
0000000352 Init===> Obj=Philo::inst[4],State=Philo::thinking
           Obj-Dict 0x20000680->Table::inst
           Sig-Dict 00000006,Obj=0x00000000->DONE_SIG
           Sig-Dict 00000005,Obj=0x00000000->EAT_SIG
           Sig-Dict 00000007,Obj=0x00000000->PAUSE_SIG
           Sig-Dict 00000008,Obj=0x00000000->SERVE_SIG
           Sig-Dict 00000009,Obj=0x00000000->TEST_SIG
           Sig-Dict 00000011,Obj=0x20000680->HUNGRY_SIG
0000000370 AO-Subsc Obj=Table::inst,Sig=DONE_SIG
0000000370 AO-Subsc Obj=Table::inst,Sig=PAUSE_SIG
0000000370 AO-Subsc Obj=Table::inst,Sig=SERVE_SIG
0000000371 AO-Subsc Obj=Table::inst,Sig=TEST_SIG
0000000371 PHILO_STAT 0 thinking
0000000371 PHILO_STAT 1 thinking
0000000371 PHILO_STAT 2 thinking
0000000371 PHILO_STAT 3 thinking
```


