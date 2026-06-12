---
title: "Disappearing harddrive, SATA"
date: 2010-02-07
forum: General Help
---

### Post by EddieX on 2010-02-07
Hi,

For a couple of weeks ago I installed a new harddrive in my server and everything was running smoothly until the new harddrive disappears from /dev. It has now happened twice and regarding the SMART-status for the drive it seems healthy, so I'm starting to think that this might be kernel-related (or disc-related?) since the other drives attached to the controller works just fine.

I have done some searching on google and I have found out that there has been some issues like this reported, but they should be fixed/solved by now.

Any ideas? Any suggestions ?

Thanks in advance!
/Eddie

--- LOGS & INFO ---
**Ubuntu:**Server 9.04 64bit
**Kernel:** 2.6.31-17-server
**SATA-controller:**Promise SATA300 TX4
**smartctl -a /dev/hdc**
```

root@hemma:~# smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD15EARS-00Z5B1
Serial Number:    WD-WMAVU1360370
Firmware Version: 80.00A80
User Capacity:    1 500 301 910 016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb  7 11:44:31 2010 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (31200) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3031)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   184   181   021    Pre-fail  Always       -       5758
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       17
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       245
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       15
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       13
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5165
194 Temperature_Celsius     0x0022   120   117   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       205         -
# 2  Short offline       Completed without error       00%        38         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

**dmesg gives:**
```

[609489.600286] ata4.00: detaching (SCSI 3:0:0:0)
[609489.600718] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
[609489.604308] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[609489.604321] sd 3:0:0:0: [sdc] Stopping disk
[609489.604358] sd 3:0:0:0: [sdc] START_STOP FAILED
[609489.604362] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
....
[609790.221072] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen
[609790.221091] ata4: hotplug_status 0x44
[609790.221123] ata4: hard resetting link
[609796.010043] ata4: link is slow to respond, please be patient (ready=-19)
[609800.270040] ata4: COMRESET failed (errno=-16)
[609800.270070] ata4: hard resetting link
[609806.060026] ata4: link is slow to respond, please be patient (ready=-19)
[609810.320028] ata4: COMRESET failed (errno=-16)
[609810.320057] ata4: hard resetting link
[609816.110026] ata4: link is slow to respond, please be patient (ready=-19)
[609845.330029] ata4: COMRESET failed (errno=-16)
[609845.330053] ata4: limiting SATA link speed to 1.5 Gbps
[609845.330066] ata4: hard resetting link
[609850.340033] ata4: COMRESET failed (errno=-16)
[609850.340053] ata4: reset failed, giving up
[609850.340079] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen t4
[609850.340104] ata4: hotplug_status 0x40
[609850.340133] ata4: hard resetting link
[609856.130043] ata4: link is slow to respond, please be patient (ready=-19)
[609860.390034] ata4: COMRESET failed (errno=-16)
[609860.390064] ata4: hard resetting link
[609866.180031] ata4: link is slow to respond, please be patient (ready=-19)
[609870.440025] ata4: COMRESET failed (errno=-16)
[609870.440054] ata4: hard resetting link
[609876.230045] ata4: link is slow to respond, please be patient (ready=-19)
[609905.450033] ata4: COMRESET failed (errno=-16)
[609905.450056] ata4: limiting SATA link speed to 1.5 Gbps
[609905.450070] ata4: hard resetting link
[609910.460027] ata4: COMRESET failed (errno=-16)
[609910.460048] ata4: reset failed, giving up
[609910.460078] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen t3
[609910.460098] ata4: hotplug_status 0x40
[609910.460126] ata4: hard resetting link
[609916.250048] ata4: link is slow to respond, please be patient (ready=-19)
[609920.510034] ata4: COMRESET failed (errno=-16)
[609920.510063] ata4: hard resetting link
[609926.300027] ata4: link is slow to respond, please be patient (ready=-19)
[609930.560046] ata4: COMRESET failed (errno=-16)
[609930.560075] ata4: hard resetting link
[609936.350031] ata4: link is slow to respond, please be patient (ready=-19)
[609965.570028] ata4: COMRESET failed (errno=-16)
[609965.570051] ata4: limiting SATA link speed to 1.5 Gbps
[609965.570065] ata4: hard resetting link
[609970.580047] ata4: COMRESET failed (errno=-16)
[609970.580069] ata4: reset failed, giving up
[609970.580094] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen t2
[609970.580114] ata4: hotplug_status 0x44
[609970.580142] ata4: hard resetting link
[609976.370026] ata4: link is slow to respond, please be patient (ready=-19)
[609980.630027] ata4: COMRESET failed (errno=-16)
[609980.630056] ata4: hard resetting link
[609986.420050] ata4: link is slow to respond, please be patient (ready=-19)
[609990.680024] ata4: COMRESET failed (errno=-16)
[609990.680052] ata4: hard resetting link
[609996.470040] ata4: link is slow to respond, please be patient (ready=-19)
[610025.690033] ata4: COMRESET failed (errno=-16)
[610025.690056] ata4: limiting SATA link speed to 1.5 Gbps
[610025.690069] ata4: hard resetting link
[610030.700028] ata4: COMRESET failed (errno=-16)
[610030.700049] ata4: reset failed, giving up
[610030.700075] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen t1
[610030.700101] ata4: hotplug_status 0x44
[610030.700128] ata4: hard resetting link
[610036.490034] ata4: link is slow to respond, please be patient (ready=-19)
[610040.750032] ata4: COMRESET failed (errno=-16)
[610040.750061] ata4: hard resetting link
[610046.540028] ata4: link is slow to respond, please be patient (ready=-19)
[610050.800037] ata4: COMRESET failed (errno=-16)
[610050.800066] ata4: hard resetting link
[610056.590052] ata4: link is slow to respond, please be patient (ready=-19)
[610085.810029] ata4: COMRESET failed (errno=-16)
[610085.810052] ata4: limiting SATA link speed to 1.5 Gbps
[610085.810067] ata4: hard resetting link
[610090.820034] ata4: COMRESET failed (errno=-16)
[610090.820054] ata4: reset failed, giving up
[610090.820070] ata4: EH pending after 5 tries, giving up
[610090.820084] ata4: EH complete

```

**lspci for controller:**
```

03:10.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)
	Subsystem: Promise Technology, Inc. PDC40718 (SATA 300 TX4)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 72 (1000ns min, 4500ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at ec00 [size=128]
	Region 2: I/O ports at e800 [size=256]
	Region 3: Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at feac0000 (32-bit, non-prefetchable) [size=128K]
	Expansion ROM at feae0000 [disabled] [size=32K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: sata_promise


```

---

