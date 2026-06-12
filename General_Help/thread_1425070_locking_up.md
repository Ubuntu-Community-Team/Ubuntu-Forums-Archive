---
title: "locking up"
date: 2010-03-08
forum: General Help
---

### Post by spetroff on 2010-03-08
How do I go about diagnosing my 9.10 Studio machine (AMD XP2500+ 2GB)? The system randomly locks up about once a week, but there is no particular action which seems to be the cause. Is there any kind of logging going on by default which can help me figure out what is going wrong? What kind of additional logging can I do to help diagnose this thing? Thanks

Shane

---

### Post by richardjh on 2010-03-08
Log files are written to /var/log/

If you don't know where to start, then start with /var/log/messages.

If you can pinpoint the time of the error, it should be possible to track down any errors for that time in the logs.

---

### Post by spetroff on 2010-03-14
Thanks for the advice.

The messages file contains a couple potential issues, in particular a whack of errors like:

[I]Mar 14 21:38:13 cesium kernel: [544654.053930] Xorg:4766 freeing invalid memtype e06b5000-e06c5000
[/I]
the timestamp on them seems quite close to the crash. The syslog and kern.log also seems to contain the same data regarding these errors. Searching the forums for "freeing invalid memtype" doesn't yield much though.

kern.log has a couple more errors/warnings a little later

[I]Mar 14 21:41:12 cesium kernel: [   25.209212] [drm] Initialized drm 1.1.0 20060810
Mar 14 21:41:12 cesium kernel: [   25.234640] matrox_w1 0000:03:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
Mar 14 21:41:12 cesium kernel: [   25.234841] [drm] Initialized mga 3.2.1 20051102 for 0000:03:00.0 on minor 0
Mar 14 21:41:12 cesium kernel: [   25.238987] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
Mar 14 21:41:12 cesium kernel: [   25.241059] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 1x mode
Mar 14 21:41:12 cesium kernel: [   25.241144] matrox_w1 0000:03:00.0: putting AGP V2 device into 1x mode
Mar 14 21:41:12 cesium kernel: [   25.278654] [drm] Initialized card for AGP DMA.
Mar 14 21:42:06 cesium kernel: [   79.475380] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[/I]
On older logs I see:

[I]Mar  7 07:52:51 cesium rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1626" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar  7 15:34:50 cesium kernel: [543870.805070] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar  7 15:34:50 cesium kernel: [543870.805080] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Mar  7 15:34:50 cesium kernel: [543870.805086] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
...
Mar  8 13:21:03 cesium kernel: [    3.110102] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[ed003000-ed0037ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Mar  8 13:21:03 cesium kernel: [    3.144299]  unknown partition table
Mar  8 13:21:03 cesium kernel: [    3.145048] md: bind<sda2>
Mar  8 13:21:03 cesium kernel: [    3.149639]  unknown partition table
Mar  8 13:21:03 cesium kernel: [    3.157882] raid1: raid set md1 active with 2 out of 2 mirrors
Mar  8 13:21:03 cesium kernel: [    3.157922] md1: detected capacity change from 0 to 3002138624
Mar  8 13:21:03 cesium kernel: [    3.160748]  md1: unknown partition table[/I]

Other than that, there doesn't seem to be much of interest in there.

---

