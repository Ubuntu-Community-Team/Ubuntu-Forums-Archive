---
title: "MDADM Brand New Disk Failures"
date: 2010-06-19
forum: General Help
---

### Post by ViPeRaY on 2010-06-19
Hey folks,

I currently have a Raid0 setup with two disks and I have no problems whatsover. I currently bought 3 brand new 1B drives and I set up Raid5. I created the array and everything works fine. I formatted the array and mounted it. When I tried to copy 750gb of data over my new array, it copies fine at some point and it fails. After reboot, I am seeing the array inactive. I tried everything and could not get the raid back active status. I have removed the array and recreated again, formatted again. When I started copying my files over, exactly same thing happened. Please see below, it shows at some point, the devices are failing.

```

Jun 19 12:54:40 VIPERLNX kernel: [  235.390079] md: super_written gets error=-5, uptodate=0
Jun 19 12:54:40 VIPERLNX kernel: [  235.390082] raid5: Disk failure on sda1, disabling device.
Jun 19 12:54:40 VIPERLNX kernel: [  235.390083] raid5: Operation continuing on 2 devices.
Jun 19 12:54:40 VIPERLNX kernel: [  235.390121] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 19 12:54:40 VIPERLNX kernel: [  235.390129] ata2: EH complete
Jun 19 12:54:40 VIPERLNX kernel: [  235.390136] sd 1:0:0:0: [sdb] Unhandled error code
Jun 19 12:54:40 VIPERLNX kernel: [  235.390137] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 19 12:54:40 VIPERLNX kernel: [  235.390140] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 74 70 59 3f 00 00 08 00
Jun 19 12:54:40 VIPERLNX kernel: [  235.390145] end_request: I/O error, dev sdb, sector 1953519935
Jun 19 12:54:40 VIPERLNX kernel: [  235.390155] end_request: I/O error, dev sdb, sector 1953519935
Jun 19 12:54:40 VIPERLNX kernel: [  235.390157] md: super_written gets error=-5, uptodate=0
Jun 19 12:54:40 VIPERLNX kernel: [  235.390159] raid5: Disk failure on sdb1, disabling device.
Jun 19 12:54:40 VIPERLNX kernel: [  235.390160] raid5: Operation continuing on 1 devices.
Jun 19 12:54:41 VIPERLNX kernel: [  235.415111] RAID5 conf printout:
Jun 19 12:54:41 VIPERLNX kernel: [  235.415114]  --- rd:3 wd:1
Jun 19 12:54:41 VIPERLNX kernel: [  235.415116]  disk 0, o:0, dev:sda1
Jun 19 12:54:41 VIPERLNX kernel: [  235.415119]  disk 1, o:0, dev:sdb1
Jun 19 12:54:41 VIPERLNX kernel: [  235.415121]  disk 2, o:1, dev:sdf1
Jun 19 12:54:41 VIPERLNX kernel: [  235.551255] RAID5 conf printout:
Jun 19 12:54:41 VIPERLNX kernel: [  235.551257]  --- rd:3 wd:1
Jun 19 12:54:41 VIPERLNX kernel: [  235.551259]  disk 0, o:0, dev:sda1
Jun 19 12:54:41 VIPERLNX kernel: [  235.551261]  disk 2, o:1, dev:sdf1
Jun 19 12:54:41 VIPERLNX kernel: [  235.551269] RAID5 conf printout:
Jun 19 12:54:41 VIPERLNX kernel: [  235.551270]  --- rd:3 wd:1
Jun 19 12:54:41 VIPERLNX kernel: [  235.551272]  disk 0, o:0, dev:sda1
Jun 19 12:54:41 VIPERLNX kernel: [  235.551274]  disk 2, o:1, dev:sdf1
Jun 19 12:54:41 VIPERLNX kernel: [  235.631255] RAID5 conf printout:
Jun 19 12:54:41 VIPERLNX kernel: [  235.631257]  --- rd:3 wd:1
Jun 19 12:54:41 VIPERLNX kernel: [  235.631259]  disk 2, o:1, dev:sdf1
Jun 19 12:54:41 VIPERLNX kernel: [  235.631273] __ratelimit: 9 callbacks suppressed
Jun 19 12:54:41 VIPERLNX kernel: [  235.631277] Buffer I/O error on device md5, logical block 283115560
Jun 19 12:54:41 VIPERLNX kernel: [  235.631279] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631291] Buffer I/O error on device md5, logical block 283115581
Jun 19 12:54:41 VIPERLNX kernel: [  235.631293] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631303] Buffer I/O error on device md5, logical block 283123883
Jun 19 12:54:41 VIPERLNX kernel: [  235.631305] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631312] Buffer I/O error on device md5, logical block 68
Jun 19 12:54:41 VIPERLNX kernel: [  235.631314] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631321] Buffer I/O error on device md5, logical block 1035
Jun 19 12:54:41 VIPERLNX kernel: [  235.631323] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631329] Buffer I/O error on device md5, logical block 1036
Jun 19 12:54:41 VIPERLNX kernel: [  235.631331] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631338] Buffer I/O error on device md5, logical block 1037
Jun 19 12:54:41 VIPERLNX kernel: [  235.631340] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631346] Buffer I/O error on device md5, logical block 1038
Jun 19 12:54:41 VIPERLNX kernel: [  235.631348] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631355] Buffer I/O error on device md5, logical block 1039
Jun 19 12:54:41 VIPERLNX kernel: [  235.631357] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631363] Buffer I/O error on device md5, logical block 1040
Jun 19 12:54:41 VIPERLNX kernel: [  235.631365] lost page write due to I/O error on md5
Jun 19 12:54:41 VIPERLNX kernel: [  235.631984] Aborting journal on device md5-8.
Jun 19 12:54:41 VIPERLNX kernel: [  235.632216] JBD2: I/O error detected when updating journal superblock for md5-8.
Jun 19 12:54:41 VIPERLNX kernel: [  235.646867] EXT4-fs error (device md5) in ext4_da_writepages: IO failure
Jun 19 12:54:41 VIPERLNX kernel: [  235.647042] EXT4-fs error (device md5): ext4_journal_start_sb: Detected aborted journal
Jun 19 12:54:41 VIPERLNX kernel: [  235.647046] EXT4-fs (md5): Remounting filesystem read-only
Jun 19 12:54:41 VIPERLNX kernel: [  235.647048] EXT4-fs (md5): ext4_da_writepages: jbd2_start: 30784 pages, ino 70779365; err -30
Jun 19 12:54:41 VIPERLNX kernel: [  235.647051] 
Jun 19 12:54:41 VIPERLNX kernel: [  235.647154] EXT4-fs error (device md5) in ext4_da_writepages: IO failure
Jun 19 12:54:41 VIPERLNX kernel: [  235.647159] EXT4-fs (md5): ext4_da_writepages: jbd2_start: 30720 pages, ino 70779364; err -30
Jun 19 12:54:41 VIPERLNX kernel: [  235.647162] 
Jun 19 12:54:41 VIPERLNX kernel: [  235.688793] JBD2: Detected IO errors while flushing file data on md5-8
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953966] ata15: drained 256 bytes to clear DRQ.
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953971] ata15.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953974] ata15.00: failed command: IDENTIFY DEVICE
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953978] ata15.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953979]          res 40/00:00:3c:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953981] ata15.00: status: { DRDY }
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953986] ata15: hard resetting link
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.953987] ata15: nv: skipping hardreset on occupied port
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982727] ata16: drained 256 bytes to clear DRQ.
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982731] ata16.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982733] ata16.00: failed command: IDENTIFY DEVICE
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982737] ata16.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982738]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982740] ata16.00: status: { DRDY }
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982744] ata16: hard resetting link
Jun 19 13:21:17 VIPERLNX kernel: [ 1831.982745] ata16: nv: skipping hardreset on occupied port
Jun 19 13:21:18 VIPERLNX kernel: [ 1832.440031] ata15: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 13:21:18 VIPERLNX kernel: [ 1832.470031] ata16: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.470016] ata15.00: qc timeout (cmd 0x27)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.470021] ata15.00: failed to read native max address (err_mask=0x4)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.470023] ata15.00: revalidation failed (errno=-5)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.470029] ata15: hard resetting link
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.470031] ata15: nv: skipping hardreset on occupied port
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.490016] ata16.00: qc timeout (cmd 0x27)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.490020] ata16.00: failed to read native max address (err_mask=0x4)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.490023] ata16.00: revalidation failed (errno=-5)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.490028] ata16: hard resetting link
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.490029] ata16: nv: skipping hardreset on occupied port
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.950034] ata15: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 13:21:23 VIPERLNX kernel: [ 1837.980032] ata16: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 19 13:21:33 VIPERLNX kernel: [ 1847.970019] ata15.00: qc timeout (cmd 0x27)
Jun 19 13:21:33 VIPERLNX kernel: [ 1847.970023] ata15.00: failed to read native max address (err_mask=0x4)
Jun 19 13:21:33 VIPERLNX kernel: [ 1847.970026] ata15.00: revalidation failed (errno=-5)
Jun 19 13:21:33 VIPERLNX kernel: [ 1847.970029] ata15: limiting SATA link speed to 1.5 Gbps
Jun 19 13:21:33 VIPERLNX kernel: [ 1847.970034] ata15: hard resetting link
Jun 19 13:21:33 VIPERLNX kernel: [ 1847.970036] ata15: nv: skipping hardreset on occupied port
Jun 19 13:21:33 VIPERLNX kernel: [ 1848.000016] ata16.00: qc timeout (cmd 0x27)
Jun 19 13:21:33 VIPERLNX kernel: [ 1848.000020] ata16.00: failed to read native max address (err_mask=0x4)
Jun 19 13:21:33 VIPERLNX kernel: [ 1848.000022] ata16.00: revalidation failed (errno=-5)
Jun 19 13:21:33 VIPERLNX kernel: [ 1848.000025] ata16: limiting SATA link speed to 1.5 Gbps
Jun 19 13:21:33 VIPERLNX kernel: [ 1848.000030] ata16: hard resetting link
Jun 19 13:21:33 VIPERLNX kernel: [ 1848.000031] ata16: nv: skipping hardreset on occupied port
Jun 19 13:21:34 VIPERLNX kernel: [ 1848.460033] ata15: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 13:21:34 VIPERLNX kernel: [ 1848.490032] ata16: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.480020] ata15.00: qc timeout (cmd 0x27)
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.480025] ata15.00: failed to read native max address (err_mask=0x4)
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.480027] ata15.00: revalidation failed (errno=-5)
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.480030] ata15.00: disabled
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.480042] ata15: hard resetting link
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.510019] ata16.00: qc timeout (cmd 0x27)
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.510022] ata16.00: failed to read native max address (err_mask=0x4)
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.510025] ata16.00: revalidation failed (errno=-5)
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.510027] ata16.00: disabled
Jun 19 13:21:44 VIPERLNX kernel: [ 1858.510037] ata16: hard resetting link
Jun 19 13:21:45 VIPERLNX kernel: [ 1859.390034] ata15: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 19 13:21:45 VIPERLNX kernel: [ 1859.390049] ata15: EH complete
Jun 19 13:21:45 VIPERLNX kernel: [ 1859.420032] ata16: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 19 13:21:45 VIPERLNX kernel: [ 1859.420046] ata16: EH complete

``````

:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md5 : inactive sdf1[2](S) sdb1[1](S) sda1[0](S)
      2930279808 blocks
       
md1 : active raid0 sdc1[1] sdd1[0]
      1465143808 blocks 64k chunks
      
unused devices: <none>


```Is there any ideas? I am not sure why the devices are failing.
P.S. I am using Ubuntu 10.04 64 bit with every updates installed.

Thanks a lot,

---

### Post by cariboo on 2010-06-19
Are you using software raid, or fakeraid?

---

### Post by ViPeRaY on 2010-06-19
I apologize, I forgot to give you that info. I am using software raid. I am using mdadm tool.

---

### Post by ViPeRaY on 2010-06-20
Hey guys,

This time I used four hard drives. I used following to create the raid.
sudo mdadm --create --verbose /dev/md2 --level=raid5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sde1 /dev/sdf1

Here is the log from the creation of the raid and until it breaks. If you review the logs, it works and devices start to fail. Then it stops.

```

Jun 20 13:39:22 VIPERLNX kernel: [  999.192398] md: bind<sda1>
Jun 20 13:39:22 VIPERLNX kernel: [  999.194725] md: bind<sdb1>
Jun 20 13:39:22 VIPERLNX kernel: [  999.196991] md: bind<sde1>
Jun 20 13:39:22 VIPERLNX kernel: [  999.199220] md: bind<sdf1>
Jun 20 13:39:22 VIPERLNX kernel: [  999.222845] raid5: device sde1 operational as raid disk 2
Jun 20 13:39:22 VIPERLNX kernel: [  999.222847] raid5: device sdb1 operational as raid disk 1
Jun 20 13:39:22 VIPERLNX kernel: [  999.222849] raid5: device sda1 operational as raid disk 0
Jun 20 13:39:22 VIPERLNX kernel: [  999.223180] raid5: allocated 4282kB for md0
Jun 20 13:39:22 VIPERLNX kernel: [  999.226563] 2: w=1 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Jun 20 13:39:22 VIPERLNX kernel: [  999.226565] 1: w=2 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Jun 20 13:39:22 VIPERLNX kernel: [  999.226568] 0: w=3 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
Jun 20 13:39:22 VIPERLNX kernel: [  999.226570] raid5: raid level 5 set md0 active with 3 out of 4 devices, algorithm 2
Jun 20 13:39:22 VIPERLNX kernel: [  999.226572] RAID5 conf printout:
Jun 20 13:39:22 VIPERLNX kernel: [  999.226573]  --- rd:4 wd:3
Jun 20 13:39:22 VIPERLNX kernel: [  999.226574]  disk 0, o:1, dev:sda1
Jun 20 13:39:22 VIPERLNX kernel: [  999.226576]  disk 1, o:1, dev:sdb1
Jun 20 13:39:22 VIPERLNX kernel: [  999.226577]  disk 2, o:1, dev:sde1
Jun 20 13:39:22 VIPERLNX kernel: [  999.226603] md0: detected capacity change from 0 to 3000606523392
Jun 20 13:39:22 VIPERLNX kernel: [  999.229068] RAID5 conf printout:
Jun 20 13:39:22 VIPERLNX kernel: [  999.229071]  --- rd:4 wd:3
Jun 20 13:39:22 VIPERLNX kernel: [  999.229073]  disk 0, o:1, dev:sda1
Jun 20 13:39:22 VIPERLNX kernel: [  999.229074]  disk 1, o:1, dev:sdb1
Jun 20 13:39:22 VIPERLNX kernel: [  999.229076]  disk 2, o:1, dev:sde1
Jun 20 13:39:22 VIPERLNX kernel: [  999.229077]  disk 3, o:1, dev:sdf1
Jun 20 13:39:22 VIPERLNX kernel: [  999.230793] md: recovery of RAID array md0
Jun 20 13:39:22 VIPERLNX kernel: [  999.230796] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Jun 20 13:39:22 VIPERLNX kernel: [  999.230798] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
Jun 20 13:39:22 VIPERLNX kernel: [  999.230802] md: using 128k window, over a total of 976759936 blocks.
Jun 20 13:39:22 VIPERLNX kernel: [  999.234626]  md0: unknown partition table
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950610] ata14: EH in SWNCQ mode,QC:qc_active 0x3 sactive 0x3
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950613] ata14: SWNCQ:qc_active 0x1 defer_bits 0x2 last_issue_tag 0x0
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950614]   dhfis 0x0 dmafis 0x0 sdbfis 0x0
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950617] ata13: EH in SWNCQ mode,QC:qc_active 0x187 sactive 0x187
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950620] ata14: ATA_REG 0x40 ERR_REG 0x0
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950621] ata14: tag : dhfis dmafis sdbfis sacitve
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950623] ata14: tag 0x0: 0 0 0 1  
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950626] ata13: SWNCQ:qc_active 0x80 defer_bits 0x107 last_issue_tag 0x7
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950626]   dhfis 0x0 dmafis 0x0 sdbfis 0x0
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950629] ata13: ATA_REG 0x40 ERR_REG 0x0
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950631] ata14.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950634] ata13: tag : dhfis dmafis sdbfis sacitve
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950635] ata14.00: failed command: WRITE FPDMA QUEUED
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950640] ata14.00: cmd 61/a0:00:9f:25:dd/03:00:06:00:00/40 tag 0 ncq 475136 out
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950641]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950643] ata14.00: status: { DRDY }
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950646] ata13: tag 0x7: 0 0 0 1  
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950647] ata14.00: failed command: WRITE FPDMA QUEUED
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950651] ata14.00: cmd 61/c8:08:3f:29:dd/00:00:06:00:00/40 tag 1 ncq 102400 out
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950652]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950654] ata14.00: status: { DRDY }
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950660] ata14: hard resetting link
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950661] ata14: nv: skipping hardreset on occupied port
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950664] ata13.00: exception Emask 0x0 SAct 0x187 SErr 0x0 action 0x6 frozen
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950666] ata13.00: failed command: READ FPDMA QUEUED
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950670] ata13.00: cmd 60/00:00:3f:2b:dd/01:00:06:00:00/40 tag 0 ncq 131072 in
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950671]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950673] ata13.00: status: { DRDY }
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950675] ata13.00: failed command: READ FPDMA QUEUED
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950679] ata13.00: cmd 60/00:08:3f:2c:dd/01:00:06:00:00/40 tag 1 ncq 131072 in
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950679]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950681] ata13.00: status: { DRDY }
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950683] ata13.00: failed command: READ FPDMA QUEUED
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950687] ata13.00: cmd 60/60:10:3f:2d:dd/00:00:06:00:00/40 tag 2 ncq 49152 in
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950688]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950690] ata13.00: status: { DRDY }
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950692] ata13.00: failed command: READ FPDMA QUEUED
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950695] ata13.00: cmd 60/38:38:07:2a:dd/00:00:06:00:00/40 tag 7 ncq 28672 in
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950696]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950698] ata13.00: status: { DRDY }
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950700] ata13.00: failed command: READ FPDMA QUEUED
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950704] ata13.00: cmd 60/00:40:3f:2a:dd/01:00:06:00:00/40 tag 8 ncq 131072 in
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950704]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950706] ata13.00: status: { DRDY }
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950711] ata13: hard resetting link
Jun 20 13:51:03 VIPERLNX kernel: [ 1699.950712] ata13: nv: skipping hardreset on occupied port
Jun 20 13:51:03 VIPERLNX kernel: [ 1700.443173] ata13: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 20 13:51:03 VIPERLNX kernel: [ 1700.450065] ata14: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.461321] ata13.00: qc timeout (cmd 0x27)
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.461326] ata13.00: failed to read native max address (err_mask=0x4)
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.461328] ata13.00: revalidation failed (errno=-5)
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.461335] ata13: hard resetting link
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.461336] ata13: nv: skipping hardreset on occupied port
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.470028] ata14.00: qc timeout (cmd 0x27)
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.470032] ata14.00: failed to read native max address (err_mask=0x4)
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.470034] ata14.00: revalidation failed (errno=-5)
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.470041] ata14: hard resetting link
Jun 20 13:51:08 VIPERLNX kernel: [ 1705.470042] ata14: nv: skipping hardreset on occupied port
Jun 20 13:51:09 VIPERLNX kernel: [ 1705.953195] ata13: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 20 13:51:09 VIPERLNX kernel: [ 1705.961693] ata14: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.970845] ata13.00: qc timeout (cmd 0x27)
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.970850] ata13.00: failed to read native max address (err_mask=0x4)
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.970854] ata13.00: revalidation failed (errno=-5)
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.970858] ata13: limiting SATA link speed to 1.5 Gbps
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.970864] ata13: hard resetting link
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.970866] ata13: nv: skipping hardreset on occupied port
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.983234] ata14.00: qc timeout (cmd 0x27)
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.983239] ata14.00: failed to read native max address (err_mask=0x4)
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.983243] ata14.00: revalidation failed (errno=-5)
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.983247] ata14: limiting SATA link speed to 1.5 Gbps
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.983253] ata14: hard resetting link
Jun 20 13:51:19 VIPERLNX kernel: [ 1715.983255] ata14: nv: skipping hardreset on occupied port
Jun 20 13:51:19 VIPERLNX kernel: [ 1716.461283] ata13: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 20 13:51:19 VIPERLNX kernel: [ 1716.472551] ata14: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481271] ata13.00: qc timeout (cmd 0x27)
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481276] ata13.00: failed to read native max address (err_mask=0x4)
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481279] ata13.00: revalidation failed (errno=-5)
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481282] ata13.00: disabled
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481333] ata13.00: device reported invalid CHS sector 0
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481388] ata13.00: device reported invalid CHS sector 0
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481405] ata13.00: device reported invalid CHS sector 0
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481418] ata13.00: device reported invalid CHS sector 0
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481462] ata13.00: device reported invalid CHS sector 0
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.481470] ata13: hard resetting link
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.492290] ata14.00: qc timeout (cmd 0x27)
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.492295] ata14.00: failed to read native max address (err_mask=0x4)
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.492298] ata14.00: revalidation failed (errno=-5)
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.492301] ata14.00: disabled
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.492339] ata14.00: device reported invalid CHS sector 0
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.492345] ata14.00: device reported invalid CHS sector 0
Jun 20 13:51:29 VIPERLNX kernel: [ 1726.492355] ata14: hard resetting link
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392452] ata13: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392471] ata13: EH complete
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392490] sd 12:0:0:0: [sde] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392492] sd 12:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392495] sd 12:0:0:0: [sde] CDB: Read(10): 28 00 06 dd 2a 3f 00 01 00 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392504] end_request: I/O error, dev sde, sector 115157567
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392509] __ratelimit: 9 callbacks suppressed
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392511] raid5:md0: read error not correctable (sector 115157504 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392514] raid5: Disk failure on sde1, disabling device.
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392515] raid5: Operation continuing on 2 devices.
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392526] raid5:md0: read error not correctable (sector 115157512 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392530] raid5:md0: read error not correctable (sector 115157520 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392533] raid5:md0: read error not correctable (sector 115157528 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392536] raid5:md0: read error not correctable (sector 115157536 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392539] raid5:md0: read error not correctable (sector 115157544 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392542] raid5:md0: read error not correctable (sector 115157552 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392544] raid5:md0: read error not correctable (sector 115157560 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392548] raid5:md0: read error not correctable (sector 115157568 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392551] raid5:md0: read error not correctable (sector 115157576 on sde1).
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392574] sd 12:0:0:0: [sde] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392576] sd 12:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392579] sd 12:0:0:0: [sde] CDB: Read(10): 28 00 06 dd 2a 07 00 00 38 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392587] end_request: I/O error, dev sde, sector 115157511
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392598] sd 12:0:0:0: [sde] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392600] sd 12:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392603] sd 12:0:0:0: [sde] CDB: Read(10): 28 00 06 dd 2d 3f 00 00 60 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392610] end_request: I/O error, dev sde, sector 115158335
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392625] sd 12:0:0:0: [sde] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392627] sd 12:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392630] sd 12:0:0:0: [sde] CDB: Read(10): 28 00 06 dd 2c 3f 00 01 00 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392637] end_request: I/O error, dev sde, sector 115158079
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392665] sd 12:0:0:0: [sde] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392667] sd 12:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392670] sd 12:0:0:0: [sde] CDB: Read(10): 28 00 06 dd 2b 3f 00 01 00 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.392682] end_request: I/O error, dev sde, sector 115157823
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410038] ata14: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410054] ata14: EH complete
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410068] sd 13:0:0:0: [sdf] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410071] sd 13:0:0:0: [sdf] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410074] sd 13:0:0:0: [sdf] CDB: Write(10): 2a 00 06 dd 29 3f 00 00 c8 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410082] end_request: I/O error, dev sdf, sector 115157311
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410086] raid5: Disk failure on sdf1, disabling device.
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410087] raid5: Operation continuing on 2 devices.
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410111] sd 13:0:0:0: [sdf] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410113] sd 13:0:0:0: [sdf] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410116] sd 13:0:0:0: [sdf] CDB: Write(10): 2a 00 06 dd 25 9f 00 03 a0 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410124] end_request: I/O error, dev sdf, sector 115156383
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410172] sd 13:0:0:0: [sdf] Unhandled error code
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410174] sd 13:0:0:0: [sdf] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410177] sd 13:0:0:0: [sdf] CDB: Write(10): 2a 00 74 70 59 3f 00 00 08 00
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410185] end_request: I/O error, dev sdf, sector 1953519935
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410190] end_request: I/O error, dev sdf, sector 1953519935
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.410193] md: super_written gets error=-5, uptodate=0
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.420041] md: md0: recovery done.
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.438125] RAID5 conf printout:
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.438127]  --- rd:4 wd:2
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.438130]  disk 0, o:1, dev:sda1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.438132]  disk 1, o:1, dev:sdb1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.438134]  disk 2, o:0, dev:sde1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.438136]  disk 3, o:0, dev:sdf1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481265] RAID5 conf printout:
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481268]  --- rd:4 wd:2
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481270]  disk 0, o:1, dev:sda1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481273]  disk 1, o:1, dev:sdb1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481275]  disk 2, o:0, dev:sde1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481285] RAID5 conf printout:
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481286]  --- rd:4 wd:2
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481288]  disk 0, o:1, dev:sda1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481290]  disk 1, o:1, dev:sdb1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.481292]  disk 2, o:0, dev:sde1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.521318] RAID5 conf printout:
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.521320]  --- rd:4 wd:2
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.521322]  disk 0, o:1, dev:sda1
Jun 20 13:51:30 VIPERLNX kernel: [ 1727.521324]  disk 1, o:1, dev:sdb1

```

---

