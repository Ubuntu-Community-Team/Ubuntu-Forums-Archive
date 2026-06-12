---
title: "mount ext3 raid1 drive"
date: 2011-08-10
forum: General Help
---

### Post by macdalor on 2011-08-10
Hi all,

I am new to ubuntu so please go easy on me... ;)

I have bought a ICYBOX IB-NAS4220-B a while ago and kept getting issues with it (going down and not restarting, very slow etc). 2 weeks ago one more issue arose and I couldn't restart or reconnect to the box so decided to take the disks out and recover my data to a 5BIG Lacie.

The IcyBox uses a software RAID1 and format drives in EXT3.

Being a Linux system I thought I could easily recover data from an Ubuntu box so installed the latest version as CD boot wouldn't give me satisfactory results.

I am now stuck with both 1TB drive plugged into my Ubuntu machine and can't seem to be able to mount the drives.

I have tried:
```

root@ubuntu-test:/home/ubuntu# mdadm --assemble --scan
mdadm: /dev/md0 is already in use.

``````
root@ubuntu-test:/home/ubuntu# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd2[0] sdb2[2](S)
      975972736 blocks [2/1] [U_]
      
md0 : active raid1 sdb1[1]
      530048 blocks [2/1] [_U]
      
unused devices: <none>

``````
root@ubuntu-test:/mnt# mount /dev/md1 raid -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``````
root@ubuntu-test:/home/ubuntu# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1b79e76b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78150712+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009df55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          66      530144+  fd  Linux raid autodetect
/dev/sdb2              67      121569   975972847+  fd  Linux raid autodetect
/dev/sdb3          121570      121601      257040   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76ad6743

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9475    76099584   83  Linux
/dev/sdc2            9475        9730     2049025    5  Extended
/dev/sdc5            9475        9730     2049024   82  Linux swap / Solaris

Disk /dev/md0: 542 MB, 542769152 bytes
2 heads, 4 sectors/track, 132512 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Unable to read /dev/sdd

```I have tried mounting the drive from Disk Utility and it tells me that the "Filesystem driver is not installed".

I am now stuck and would appreciate any help offered.

I hope all this make sense...:)

Thank you in advanced

---

### Post by psusi on 2011-08-10
Look for more detailed errors in dmesg, and what does mdadm -D /dev/md1 show?

It is very strange that fdisk -l couldn't read /dev/sdd.  Check the SMART stats in the disk utility and see if it is failing.

---

### Post by macdalor on 2011-08-11
> **psusi said:**
> Look for more detailed errors in dmesg, and what does mdadm -D /dev/md1 show?

It is very strange that fdisk -l couldn't read /dev/sdd.  Check the SMART stats in the disk utility and see if it is failing.

Thank you for your reply Psusi.

dmesg gives me:
> E
[  534.163378] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[  534.163385] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  534.163392] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 f2 00 00 f0 00
[  534.163406] end_request: I/O error, dev sdd, sector 1073650
[  534.163470] JBD: Failed to read block at offset 1088
[  534.163475] JBD: IO error -5 recovering block 1088 in log
[  534.163487] JBD: Failed to read block at offset 1089
[  534.163490] JBD: IO error -5 recovering block 1089 in log
[  534.163494] JBD: Failed to read block at offset 1090
[  534.163497] JBD: IO error -5 recovering block 1090 in log
[  534.163502] JBD: Failed to read block at offset 1091
[  534.163505] JBD: IO error -5 recovering block 1091 in log
[  534.163508] JBD: Failed to read block at offset 1092
[  534.163511] JBD: IO error -5 recovering block 1092 in log
[  534.163515] JBD: Failed to read block at offset 1093
[  534.163519] JBD: IO error -5 recovering block 1093 in log
[  534.163522] JBD: Failed to read block at offset 1094
[  534.163536] JBD: IO error -5 recovering block 1094 in log
[  534.163539] JBD: Failed to read block at offset 1095
[  534.163541] JBD: IO error -5 recovering block 1095 in log
[  534.163543] JBD: Failed to read block at offset 1096
[  534.163545] JBD: IO error -5 recovering block 1096 in log
[  534.163548] JBD: Failed to read block at offset 1097
[  534.163550] JBD: IO error -5 recovering block 1097 in log
[  534.163553] JBD: Failed to read block at offset 1098
[  534.163555] JBD: IO error -5 recovering block 1098 in log
[  534.163558] JBD: Failed to read block at offset 1099
[  534.163560] JBD: IO error -5 recovering block 1099 in log
[  534.163563] JBD: Failed to read block at offset 1100
[  534.163565] JBD: IO error -5 recovering block 1100 in log
[  534.163567] JBD: Failed to read block at offset 1101
[  534.163569] JBD: IO error -5 recovering block 1101 in log
[  534.163572] JBD: Failed to read block at offset 1102
[  534.163574] JBD: IO error -5 recovering block 1102 in log
[  534.163576] JBD: Failed to read block at offset 1103
[  534.163578] JBD: IO error -5 recovering block 1103 in log
[  534.163581] JBD: Failed to read block at offset 1104
[  534.163583] JBD: IO error -5 recovering block 1104 in log
[  534.163585] JBD: Failed to read block at offset 1105
[  534.163587] JBD: IO error -5 recovering block 1105 in log
[  534.163590] JBD: Failed to read block at offset 1106
[  534.163592] JBD: IO error -5 recovering block 1106 in log
[  534.163594] JBD: Failed to read block at offset 1107
[  534.163597] JBD: IO error -5 recovering block 1107 in log
[  534.163599] JBD: Failed to read block at offset 1108
[  534.163601] JBD: IO error -5 recovering block 1108 in log
[  534.163604] JBD: Failed to read block at offset 1109
[  534.163615] JBD: IO error -5 recovering block 1109 in log
[  534.163617] JBD: Failed to read block at offset 1110
[  534.163619] JBD: IO error -5 recovering block 1110 in log
[  534.163622] JBD: Failed to read block at offset 1111
[  534.163624] JBD: IO error -5 recovering block 1111 in log
[  534.163627] JBD: Failed to read block at offset 1112
[  534.163629] JBD: IO error -5 recovering block 1112 in log
[  534.163632] JBD: Failed to read block at offset 1113
[  534.163634] JBD: IO error -5 recovering block 1113 in log
[  534.163636] JBD: Failed to read block at offset 1114
[  534.163638] JBD: IO error -5 recovering block 1114 in log
[  534.163641] JBD: Failed to read block at offset 1115
[  534.163643] JBD: IO error -5 recovering block 1115 in log
[  534.163646] JBD: Failed to read block at offset 1116
[  534.163648] JBD: IO error -5 recovering block 1116 in log
[  534.163650] JBD: Failed to read block at offset 1117
[  534.163652] JBD: IO error -5 recovering block 1117 in log
[  538.089210] JBD: recovery failed
[  538.089218] EXT3-fs (md1): error loading journal
[  641.409730] EXT3-fs: barriers not enabled
[  644.502444] sd 6:0:0:0: [sdd] Unhandled sense code
[  644.502450] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  644.502457] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[  644.502464] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  644.502472] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 f2 00 00 f0 00
[  644.502485] end_request: I/O error, dev sdd, sector 1073650
[  644.502550] JBD: Failed to read block at offset 1088
[  644.502554] JBD: IO error -5 recovering block 1088 in log
[  644.502566] JBD: Failed to read block at offset 1089
[  644.502569] JBD: IO error -5 recovering block 1089 in log
[  644.502574] JBD: Failed to read block at offset 1090
[  644.502577] JBD: IO error -5 recovering block 1090 in log
[  644.502581] JBD: Failed to read block at offset 1091
[  644.502584] JBD: IO error -5 recovering block 1091 in log
[  644.502588] JBD: Failed to read block at offset 1092
[  644.502591] JBD: IO error -5 recovering block 1092 in log
[  644.502595] JBD: Failed to read block at offset 1093
[  644.502598] JBD: IO error -5 recovering block 1093 in log
[  644.502602] JBD: Failed to read block at offset 1094
[  644.502605] JBD: IO error -5 recovering block 1094 in log
[  644.502609] JBD: Failed to read block at offset 1095
[  644.502612] JBD: IO error -5 recovering block 1095 in log
[  644.502616] JBD: Failed to read block at offset 1096
[  644.502619] JBD: IO error -5 recovering block 1096 in log
[  644.502623] JBD: Failed to read block at offset 1097
[  644.502626] JBD: IO error -5 recovering block 1097 in log
[  644.502630] JBD: Failed to read block at offset 1098
[  644.502633] JBD: IO error -5 recovering block 1098 in log
[  644.502637] JBD: Failed to read block at offset 1099
[  644.502640] JBD: IO error -5 recovering block 1099 in log
[  644.502644] JBD: Failed to read block at offset 1100
[  644.502647] JBD: IO error -5 recovering block 1100 in log
[  644.502651] JBD: Failed to read block at offset 1101
[  644.502654] JBD: IO error -5 recovering block 1101 in log
[  644.502658] JBD: Failed to read block at offset 1102
[  644.502661] JBD: IO error -5 recovering block 1102 in log
[  644.502665] JBD: Failed to read block at offset 1103
[  644.502668] JBD: IO error -5 recovering block 1103 in log
[  644.502672] JBD: Failed to read block at offset 1104
[  644.502675] JBD: IO error -5 recovering block 1104 in log
[  644.502678] JBD: Failed to read block at offset 1105
[  644.502681] JBD: IO error -5 recovering block 1105 in log
[  644.502685] JBD: Failed to read block at offset 1106
[  644.502688] JBD: IO error -5 recovering block 1106 in log
[  644.502692] JBD: Failed to read block at offset 1107
[  644.502695] JBD: IO error -5 recovering block 1107 in log
[  644.502699] JBD: Failed to read block at offset 1108
[  644.502702] JBD: IO error -5 recovering block 1108 in log
[  644.502706] JBD: Failed to read block at offset 1109
[  644.502709] JBD: IO error -5 recovering block 1109 in log
[  644.502713] JBD: Failed to read block at offset 1110
[  644.502716] JBD: IO error -5 recovering block 1110 in log
[  644.502720] JBD: Failed to read block at offset 1111
[  644.502723] JBD: IO error -5 recovering block 1111 in log
[  644.502727] JBD: Failed to read block at offset 1112
[  644.502730] JBD: IO error -5 recovering block 1112 in log
[  644.502734] JBD: Failed to read block at offset 1113
[  644.502737] JBD: IO error -5 recovering block 1113 in log
[  644.502741] JBD: Failed to read block at offset 1114
[  644.502744] JBD: IO error -5 recovering block 1114 in log
[  644.502748] JBD: Failed to read block at offset 1115
[  644.502751] JBD: IO error -5 recovering block 1115 in log
[  644.502755] JBD: Failed to read block at offset 1116
[  644.502758] JBD: IO error -5 recovering block 1116 in log
[  644.502762] JBD: Failed to read block at offset 1117
[  644.502765] JBD: IO error -5 recovering block 1117 in log
[  648.381853] JBD: recovery failed
[  648.381862] EXT3-fs (md1): error loading journal
[  928.550220] EXT3-fs: barriers not enabled
[  931.770164] sd 6:0:0:0: [sdd] Unhandled sense code
[  931.770171] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  931.770178] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[  931.770185] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  931.770193] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 f2 00 00 f0 00
[  931.770206] end_request: I/O error, dev sdd, sector 1073650
[  931.770270] JBD: Failed to read block at offset 1088
[  931.770275] JBD: IO error -5 recovering block 1088 in log
[  931.770286] JBD: Failed to read block at offset 1089
[  931.770290] JBD: IO error -5 recovering block 1089 in log
[  931.770294] JBD: Failed to read block at offset 1090
[  931.770297] JBD: IO error -5 recovering block 1090 in log
[  931.770302] JBD: Failed to read block at offset 1091
[  931.770305] JBD: IO error -5 recovering block 1091 in log
[  931.770309] JBD: Failed to read block at offset 1092
[  931.770312] JBD: IO error -5 recovering block 1092 in log
[  931.770316] JBD: Failed to read block at offset 1093
[  931.770319] JBD: IO error -5 recovering block 1093 in log
[  931.770323] JBD: Failed to read block at offset 1094
[  931.770337] JBD: IO error -5 recovering block 1094 in log
[  931.770339] JBD: Failed to read block at offset 1095
[  931.770341] JBD: IO error -5 recovering block 1095 in log
[  931.770344] JBD: Failed to read block at offset 1096
[  931.770346] JBD: IO error -5 recovering block 1096 in log
[  931.770349] JBD: Failed to read block at offset 1097
[  931.770351] JBD: IO error -5 recovering block 1097 in log
[  931.770354] JBD: Failed to read block at offset 1098
[  931.770356] JBD: IO error -5 recovering block 1098 in log
[  931.770359] JBD: Failed to read block at offset 1099
[  931.770361] JBD: IO error -5 recovering block 1099 in log
[  931.770363] JBD: Failed to read block at offset 1100
[  931.770365] JBD: IO error -5 recovering block 1100 in log
[  931.770368] JBD: Failed to read block at offset 1101
[  931.770370] JBD: IO error -5 recovering block 1101 in log
[  931.770372] JBD: Failed to read block at offset 1102
[  931.770374] JBD: IO error -5 recovering block 1102 in log
[  931.770377] JBD: Failed to read block at offset 1103
[  931.770379] JBD: IO error -5 recovering block 1103 in log
[  931.770381] JBD: Failed to read block at offset 1104
[  931.770383] JBD: IO error -5 recovering block 1104 in log
[  931.770386] JBD: Failed to read block at offset 1105
[  931.770388] JBD: IO error -5 recovering block 1105 in log
[  931.770391] JBD: Failed to read block at offset 1106
[  931.770393] JBD: IO error -5 recovering block 1106 in log
[  931.770396] JBD: Failed to read block at offset 1107
[  931.770398] JBD: IO error -5 recovering block 1107 in log
[  931.770401] JBD: Failed to read block at offset 1108
[  931.770403] JBD: IO error -5 recovering block 1108 in log
[  931.770405] JBD: Failed to read block at offset 1109
[  931.770407] JBD: IO error -5 recovering block 1109 in log
[  931.770410] JBD: Failed to read block at offset 1110
[  931.770412] JBD: IO error -5 recovering block 1110 in log
[  931.770414] JBD: Failed to read block at offset 1111
[  931.770416] JBD: IO error -5 recovering block 1111 in log
[  931.770419] JBD: Failed to read block at offset 1112
[  931.770421] JBD: IO error -5 recovering block 1112 in log
[  931.770423] JBD: Failed to read block at offset 1113
[  931.770425] JBD: IO error -5 recovering block 1113 in log
[  931.770428] JBD: Failed to read block at offset 1114
[  931.770430] JBD: IO error -5 recovering block 1114 in log
[  931.770433] JBD: Failed to read block at offset 1115
[  931.770435] JBD: IO error -5 recovering block 1115 in log
[  931.770437] JBD: Failed to read block at offset 1116
[  931.770439] JBD: IO error -5 recovering block 1116 in log
[  931.770442] JBD: Failed to read block at offset 1117
[  931.770444] JBD: IO error -5 recovering block 1117 in log
[  935.558316] JBD: recovery failed
[  935.558324] EXT3-fs (md1): error loading journal
[  984.130433] EXT3-fs: barriers not enabled
[  987.222541] sd 6:0:0:0: [sdd] Unhandled sense code
[  987.222548] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  987.222555] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[  987.222562] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[  987.222570] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 f2 00 00 f0 00
[  987.222583] end_request: I/O error, dev sdd, sector 1073650
[  987.222646] JBD: Failed to read block at offset 1088
[  987.222650] JBD: IO error -5 recovering block 1088 in log
[  987.222662] JBD: Failed to read block at offset 1089
[  987.222665] JBD: IO error -5 recovering block 1089 in log
[  987.222669] JBD: Failed to read block at offset 1090
[  987.222673] JBD: IO error -5 recovering block 1090 in log
[  987.222677] JBD: Failed to read block at offset 1091
[  987.222680] JBD: IO error -5 recovering block 1091 in log
[  987.222684] JBD: Failed to read block at offset 1092
[  987.222687] JBD: IO error -5 recovering block 1092 in log
[  987.222691] JBD: Failed to read block at offset 1093
[  987.222694] JBD: IO error -5 recovering block 1093 in log
[  987.222698] JBD: Failed to read block at offset 1094
[  987.222701] JBD: IO error -5 recovering block 1094 in log
[  987.222715] JBD: Failed to read block at offset 1095
[  987.222717] JBD: IO error -5 recovering block 1095 in log
[  987.222720] JBD: Failed to read block at offset 1096
[  987.222722] JBD: IO error -5 recovering block 1096 in log
[  987.222724] JBD: Failed to read block at offset 1097
[  987.222727] JBD: IO error -5 recovering block 1097 in log
[  987.222729] JBD: Failed to read block at offset 1098
[  987.222731] JBD: IO error -5 recovering block 1098 in log
[  987.222734] JBD: Failed to read block at offset 1099
[  987.222736] JBD: IO error -5 recovering block 1099 in log
[  987.222738] JBD: Failed to read block at offset 1100
[  987.222740] JBD: IO error -5 recovering block 1100 in log
[  987.222743] JBD: Failed to read block at offset 1101
[  987.222745] JBD: IO error -5 recovering block 1101 in log
[  987.222748] JBD: Failed to read block at offset 1102
[  987.222750] JBD: IO error -5 recovering block 1102 in log
[  987.222753] JBD: Failed to read block at offset 1103
[  987.222755] JBD: IO error -5 recovering block 1103 in log
[  987.222758] JBD: Failed to read block at offset 1104
[  987.222760] JBD: IO error -5 recovering block 1104 in log
[  987.222762] JBD: Failed to read block at offset 1105
[  987.222764] JBD: IO error -5 recovering block 1105 in log
[  987.222767] JBD: Failed to read block at offset 1106
[  987.222769] JBD: IO error -5 recovering block 1106 in log
[  987.222772] JBD: Failed to read block at offset 1107
[  987.222774] JBD: IO error -5 recovering block 1107 in log
[  987.222777] JBD: Failed to read block at offset 1108
[  987.222779] JBD: IO error -5 recovering block 1108 in log
[  987.222782] JBD: Failed to read block at offset 1109
[  987.222784] JBD: IO error -5 recovering block 1109 in log
[  987.222786] JBD: Failed to read block at offset 1110
[  987.222788] JBD: IO error -5 recovering block 1110 in log
[  987.222791] JBD: Failed to read block at offset 1111
[  987.222793] JBD: IO error -5 recovering block 1111 in log
[  987.222796] JBD: Failed to read block at offset 1112
[  987.222798] JBD: IO error -5 recovering block 1112 in log
[  987.222800] JBD: Failed to read block at offset 1113
[  987.222802] JBD: IO error -5 recovering block 1113 in log
[  987.222805] JBD: Failed to read block at offset 1114
[  987.222807] JBD: IO error -5 recovering block 1114 in log
[  987.222809] JBD: Failed to read block at offset 1115
[  987.222812] JBD: IO error -5 recovering block 1115 in log
[  987.222814] JBD: Failed to read block at offset 1116
[  987.222816] JBD: IO error -5 recovering block 1116 in log
[  987.222819] JBD: Failed to read block at offset 1117
[  987.222821] JBD: IO error -5 recovering block 1117 in log
[  991.627687] JBD: recovery failed
[  991.627696] EXT3-fs (md1): error loading journal
[ 1012.111550] sd 6:0:0:0: [sdd] Unhandled sense code
[ 1012.111556] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1012.111561] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[ 1012.111565] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[ 1012.111570] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 c2 00 00 f0 00
[ 1012.111580] end_request: I/O error, dev sdd, sector 1073602
[ 1012.111587] Buffer I/O error on device md1, logical block 1664
[ 1012.111599] Buffer I/O error on device md1, logical block 1665
[ 1012.111603] Buffer I/O error on device md1, logical block 1666
[ 1012.111607] Buffer I/O error on device md1, logical block 1667
[ 1012.111610] Buffer I/O error on device md1, logical block 1668
[ 1012.111614] Buffer I/O error on device md1, logical block 1669
[ 1012.111617] Buffer I/O error on device md1, logical block 1670
[ 1012.111621] Buffer I/O error on device md1, logical block 1671
[ 1012.111624] Buffer I/O error on device md1, logical block 1672
[ 1012.111628] Buffer I/O error on device md1, logical block 1673
[ 1015.294929] sd 6:0:0:0: [sdd] Unhandled sense code
[ 1015.294936] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1015.294943] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[ 1015.294950] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[ 1015.294958] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 62 0a 00 00 08 00
[ 1015.294971] end_request: I/O error, dev sdd, sector 1073674
[ 1041.543486] EXT3-fs: barriers not enabled
[ 1044.769075] sd 6:0:0:0: [sdd] Unhandled sense code
[ 1044.769081] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1044.769088] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[ 1044.769095] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[ 1044.769103] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 f2 00 00 f0 00
[ 1044.769116] end_request: I/O error, dev sdd, sector 1073650
[ 1044.769180] JBD: Failed to read block at offset 1088
[ 1044.769184] JBD: IO error -5 recovering block 1088 in log
[ 1044.769196] JBD: Failed to read block at offset 1089
[ 1044.769200] JBD: IO error -5 recovering block 1089 in log
[ 1044.769204] JBD: Failed to read block at offset 1090
[ 1044.769208] JBD: IO error -5 recovering block 1090 in log
[ 1044.769212] JBD: Failed to read block at offset 1091
[ 1044.769215] JBD: IO error -5 recovering block 1091 in log
[ 1044.769219] JBD: Failed to read block at offset 1092
[ 1044.769222] JBD: IO error -5 recovering block 1092 in log
[ 1044.769227] JBD: Failed to read block at offset 1093
[ 1044.769230] JBD: IO error -5 recovering block 1093 in log
[ 1044.769234] JBD: Failed to read block at offset 1094
[ 1044.769247] JBD: IO error -5 recovering block 1094 in log
[ 1044.769250] JBD: Failed to read block at offset 1095
[ 1044.769252] JBD: IO error -5 recovering block 1095 in log
[ 1044.769255] JBD: Failed to read block at offset 1096
[ 1044.769257] JBD: IO error -5 recovering block 1096 in log
[ 1044.769260] JBD: Failed to read block at offset 1097
[ 1044.769262] JBD: IO error -5 recovering block 1097 in log
[ 1044.769265] JBD: Failed to read block at offset 1098
[ 1044.769267] JBD: IO error -5 recovering block 1098 in log
[ 1044.769270] JBD: Failed to read block at offset 1099
[ 1044.769272] JBD: IO error -5 recovering block 1099 in log
[ 1044.769274] JBD: Failed to read block at offset 1100
[ 1044.769277] JBD: IO error -5 recovering block 1100 in log
[ 1044.769279] JBD: Failed to read block at offset 1101
[ 1044.769281] JBD: IO error -5 recovering block 1101 in log
[ 1044.769284] JBD: Failed to read block at offset 1102
[ 1044.769286] JBD: IO error -5 recovering block 1102 in log
[ 1044.769288] JBD: Failed to read block at offset 1103
[ 1044.769290] JBD: IO error -5 recovering block 1103 in log
[ 1044.769293] JBD: Failed to read block at offset 1104
[ 1044.769295] JBD: IO error -5 recovering block 1104 in log
[ 1044.769297] JBD: Failed to read block at offset 1105
[ 1044.769299] JBD: IO error -5 recovering block 1105 in log
[ 1044.769302] JBD: Failed to read block at offset 1106
[ 1044.769304] JBD: IO error -5 recovering block 1106 in log
[ 1044.769306] JBD: Failed to read block at offset 1107
[ 1044.769308] JBD: IO error -5 recovering block 1107 in log
[ 1044.769311] JBD: Failed to read block at offset 1108
[ 1044.769313] JBD: IO error -5 recovering block 1108 in log
[ 1044.769315] JBD: Failed to read block at offset 1109
[ 1044.769318] JBD: IO error -5 recovering block 1109 in log
[ 1044.769320] JBD: Failed to read block at offset 1110
[ 1044.769322] JBD: IO error -5 recovering block 1110 in log
[ 1044.769325] JBD: Failed to read block at offset 1111
[ 1044.769327] JBD: IO error -5 recovering block 1111 in log
[ 1044.769329] JBD: Failed to read block at offset 1112
[ 1044.769331] JBD: IO error -5 recovering block 1112 in log
[ 1044.769334] JBD: Failed to read block at offset 1113
[ 1044.769336] JBD: IO error -5 recovering block 1113 in log
[ 1044.769339] JBD: Failed to read block at offset 1114
[ 1044.769341] JBD: IO error -5 recovering block 1114 in log
[ 1044.769343] JBD: Failed to read block at offset 1115
[ 1044.769345] JBD: IO error -5 recovering block 1115 in log
[ 1044.769348] JBD: Failed to read block at offset 1116
[ 1044.769350] JBD: IO error -5 recovering block 1116 in log
[ 1044.769353] JBD: Failed to read block at offset 1117
[ 1044.769355] JBD: IO error -5 recovering block 1117 in log
[ 1048.619589] JBD: recovery failed
[ 1048.619597] EXT3-fs (md1): error loading journal
[ 1062.064975] EXT3-fs: barriers not enabled
[ 1065.290585] sd 6:0:0:0: [sdd] Unhandled sense code
[ 1065.290592] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1065.290599] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[ 1065.290606] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[ 1065.290613] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 f2 00 00 f0 00
[ 1065.290627] end_request: I/O error, dev sdd, sector 1073650
[ 1065.290692] JBD: Failed to read block at offset 1088
[ 1065.290696] JBD: IO error -5 recovering block 1088 in log
[ 1065.290708] JBD: Failed to read block at offset 1089
[ 1065.290711] JBD: IO error -5 recovering block 1089 in log
[ 1065.290716] JBD: Failed to read block at offset 1090
[ 1065.290719] JBD: IO error -5 recovering block 1090 in log
[ 1065.290723] JBD: Failed to read block at offset 1091
[ 1065.290726] JBD: IO error -5 recovering block 1091 in log
[ 1065.290730] JBD: Failed to read block at offset 1092
[ 1065.290733] JBD: IO error -5 recovering block 1092 in log
[ 1065.290737] JBD: Failed to read block at offset 1093
[ 1065.290740] JBD: IO error -5 recovering block 1093 in log
[ 1065.290745] JBD: Failed to read block at offset 1094
[ 1065.290758] JBD: IO error -5 recovering block 1094 in log
[ 1065.290761] JBD: Failed to read block at offset 1095
[ 1065.290763] JBD: IO error -5 recovering block 1095 in log
[ 1065.290766] JBD: Failed to read block at offset 1096
[ 1065.290768] JBD: IO error -5 recovering block 1096 in log
[ 1065.290771] JBD: Failed to read block at offset 1097
[ 1065.290773] JBD: IO error -5 recovering block 1097 in log
[ 1065.290775] JBD: Failed to read block at offset 1098
[ 1065.290778] JBD: IO error -5 recovering block 1098 in log
[ 1065.290780] JBD: Failed to read block at offset 1099
[ 1065.290782] JBD: IO error -5 recovering block 1099 in log
[ 1065.290785] JBD: Failed to read block at offset 1100
[ 1065.290787] JBD: IO error -5 recovering block 1100 in log
[ 1065.290790] JBD: Failed to read block at offset 1101
[ 1065.290792] JBD: IO error -5 recovering block 1101 in log
[ 1065.290794] JBD: Failed to read block at offset 1102
[ 1065.290796] JBD: IO error -5 recovering block 1102 in log
[ 1065.290799] JBD: Failed to read block at offset 1103
[ 1065.290801] JBD: IO error -5 recovering block 1103 in log
[ 1065.290803] JBD: Failed to read block at offset 1104
[ 1065.290805] JBD: IO error -5 recovering block 1104 in log
[ 1065.290808] JBD: Failed to read block at offset 1105
[ 1065.290810] JBD: IO error -5 recovering block 1105 in log
[ 1065.290813] JBD: Failed to read block at offset 1106
[ 1065.290815] JBD: IO error -5 recovering block 1106 in log
[ 1065.290818] JBD: Failed to read block at offset 1107
[ 1065.290820] JBD: IO error -5 recovering block 1107 in log
[ 1065.290822] JBD: Failed to read block at offset 1108
[ 1065.290824] JBD: IO error -5 recovering block 1108 in log
[ 1065.290827] JBD: Failed to read block at offset 1109
[ 1065.290829] JBD: IO error -5 recovering block 1109 in log
[ 1065.290832] JBD: Failed to read block at offset 1110
[ 1065.290834] JBD: IO error -5 recovering block 1110 in log
[ 1065.290836] JBD: Failed to read block at offset 1111
[ 1065.290839] JBD: IO error -5 recovering block 1111 in log
[ 1065.290841] JBD: Failed to read block at offset 1112
[ 1065.290843] JBD: IO error -5 recovering block 1112 in log
[ 1065.290846] JBD: Failed to read block at offset 1113
[ 1065.290848] JBD: IO error -5 recovering block 1113 in log
[ 1065.290851] JBD: Failed to read block at offset 1114
[ 1065.290853] JBD: IO error -5 recovering block 1114 in log
[ 1065.290856] JBD: Failed to read block at offset 1115
[ 1065.290858] JBD: IO error -5 recovering block 1115 in log
[ 1065.290860] JBD: Failed to read block at offset 1116
[ 1065.290862] JBD: IO error -5 recovering block 1116 in log
[ 1065.290865] JBD: Failed to read block at offset 1117
[ 1065.290867] JBD: IO error -5 recovering block 1117 in log
[ 1069.189342] JBD: recovery failed
[ 1069.189350] EXT3-fs (md1): error loading journal
[ 5335.003861] EXT3-fs: barriers not enabled
[ 5338.228962] sd 6:0:0:0: [sdd] Unhandled sense code
[ 5338.228969] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5338.228976] sd 6:0:0:0: [sdd]  Sense Key : Medium Error [current] 
[ 5338.228983] sd 6:0:0:0: [sdd]  Add. Sense: Unrecovered read error
[ 5338.228990] sd 6:0:0:0: [sdd] CDB: Read(10): 28 00 00 10 61 f2 00 00 f0 00
[ 5338.229013] end_request: I/O error, dev sdd, sector 1073650
[ 5338.229065] JBD: Failed to read block at offset 1088
[ 5338.229068] JBD: IO error -5 recovering block 1088 in log
[ 5338.229079] JBD: Failed to read block at offset 1089
[ 5338.229081] JBD: IO error -5 recovering block 1089 in log
[ 5338.229084] JBD: Failed to read block at offset 1090
[ 5338.229086] JBD: IO error -5 recovering block 1090 in log
[ 5338.229089] JBD: Failed to read block at offset 1091
[ 5338.229091] JBD: IO error -5 recovering block 1091 in log
[ 5338.229094] JBD: Failed to read block at offset 1092
[ 5338.229096] JBD: IO error -5 recovering block 1092 in log
[ 5338.229099] JBD: Failed to read block at offset 1093
[ 5338.229101] JBD: IO error -5 recovering block 1093 in log
[ 5338.229104] JBD: Failed to read block at offset 1094
[ 5338.229106] JBD: IO error -5 recovering block 1094 in log
[ 5338.229108] JBD: Failed to read block at offset 1095
[ 5338.229110] JBD: IO error -5 recovering block 1095 in log
[ 5338.229113] JBD: Failed to read block at offset 1096
[ 5338.229115] JBD: IO error -5 recovering block 1096 in log
[ 5338.229118] JBD: Failed to read block at offset 1097
[ 5338.229120] JBD: IO error -5 recovering block 1097 in log
[ 5338.229122] JBD: Failed to read block at offset 1098
[ 5338.229124] JBD: IO error -5 recovering block 1098 in log
[ 5338.229127] JBD: Failed to read block at offset 1099
[ 5338.229129] JBD: IO error -5 recovering block 1099 in log
[ 5338.229131] JBD: Failed to read block at offset 1100
[ 5338.229133] JBD: IO error -5 recovering block 1100 in log
[ 5338.229136] JBD: Failed to read block at offset 1101
[ 5338.229138] JBD: IO error -5 recovering block 1101 in log
[ 5338.229141] JBD: Failed to read block at offset 1102
[ 5338.229143] JBD: IO error -5 recovering block 1102 in log
[ 5338.229145] JBD: Failed to read block at offset 1103
[ 5338.229147] JBD: IO error -5 recovering block 1103 in log
[ 5338.229150] JBD: Failed to read block at offset 1104
[ 5338.229151] JBD: IO error -5 recovering block 1104 in log
[ 5338.229154] JBD: Failed to read block at offset 1105
[ 5338.229156] JBD: IO error -5 recovering block 1105 in log
[ 5338.229159] JBD: Failed to read block at offset 1106
[ 5338.229161] JBD: IO error -5 recovering block 1106 in log
[ 5338.229163] JBD: Failed to read block at offset 1107
[ 5338.229165] JBD: IO error -5 recovering block 1107 in log
[ 5338.229168] JBD: Failed to read block at offset 1108
[ 5338.229170] JBD: IO error -5 recovering block 1108 in log
[ 5338.229172] JBD: Failed to read block at offset 1109
[ 5338.229174] JBD: IO error -5 recovering block 1109 in log
[ 5338.229177] JBD: Failed to read block at offset 1110
[ 5338.229179] JBD: IO error -5 recovering block 1110 in log
[ 5338.229182] JBD: Failed to read block at offset 1111
[ 5338.229184] JBD: IO error -5 recovering block 1111 in log
[ 5338.229186] JBD: Failed to read block at offset 1112
[ 5338.229188] JBD: IO error -5 recovering block 1112 in log
[ 5338.229191] JBD: Failed to read block at offset 1113
[ 5338.229193] JBD: IO error -5 recovering block 1113 in log
[ 5338.229195] JBD: Failed to read block at offset 1114
[ 5338.229197] JBD: IO error -5 recovering block 1114 in log
[ 5338.229200] JBD: Failed to read block at offset 1115
[ 5338.229202] JBD: IO error -5 recovering block 1115 in log
[ 5338.229204] JBD: Failed to read block at offset 1116
[ 5338.229206] JBD: IO error -5 recovering block 1116 in log
[ 5338.229209] JBD: Failed to read block at offset 1117
[ 5338.229211] JBD: IO error -5 recovering block 1117 in log
[ 5341.971857] JBD: recovery failed
[ 5341.971866] EXT3-fs (md1): error loading journal
Then mdadm -D /dev/md1:
> /dev/md1:
        Version : 0.90
  Creation Time : Tue May 18 18:05:38 2010
     Raid Level : raid1
     Array Size : 975972736 (930.76 GiB 999.40 GB)
  Used Dev Size : 975972736 (930.76 GiB 999.40 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Aug 10 19:06:29 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           UUID : 42f84fd7:bbe9b88c:56cc181f:2841b23b
         Events : 0.722521

    Number   Major   Minor   RaidDevice State
       0       8       50        0      active sync   /dev/sdd2
       1       0        0        1      removed

       2       8       18        -      spare   /dev/sdb2
Also checked the SMART data and got everything ok or n/a exept from a warning on 1 sector saying:
> "current pending sector count"
Number of sectors waiting to be remapped. If the sector waiting to be remapped is sunsequently written or read successfully, this value is decreased and the sector is not remapped.Read errors on the sector will not remap the sector, it will only be remapped on a failled write attempt. Hope it does make more sense to you than it does to me...:confused:

---

### Post by psusi on 2011-08-11
Your raid appears to already have been degraded at some point in the past and now only has the one drive, sdd, which appears to be failing.  What is the value of the pending sectors count?

---

### Post by macdalor on 2011-08-11
> **psusi said:**
> Your raid appears to already have been degraded at some point in the past and now only has the one drive, sdd, which appears to be failing.  What is the value of the pending sectors count?


Value: 1 sector

What are my options? If I still have some...

---

### Post by psusi on 2011-08-11
Hrm... it seems to have much more than that... lets run a full test:

sudo badblocks -b 512 /dev/sdd

---

### Post by macdalor on 2011-08-12
Here is the result psusi...I let you uncode it ;)

> root@ubuntu-test:/home/ubuntu# sudo badblocks -b 512 /dev/sdd
0
8
9
10
11
12
13
14
15
1073664
1073680
1073681
1073682
1073683
1073684
1073685
1073686
1073687
1141386632
1141386688
1141386689
1141386690
1141386691
1141386692
1141386693
1141386694
1141386695
I think it is worth mentioning that I have made a test, just because you mentioned it was strange that fdisk -l couldn't read /dev/sdd, to swap the connections of both drives, one (sdb) being connected internally and the second (sdd) through a SATA to USB adapter. And to my surprise connecting the sdd internally kept the PC to boot up and left it on a black screen with a flashing prompt...
Not too sure if this means anything since I can see the USB connected drive from disk utility but thought I'd just mention it...just in case...

---

### Post by psusi on 2011-08-12
Those are all of the bad sectors it found.  They include sector 0, which is why fdisk can't read the partition table.

I think at this point, you're going to have to restore from backup to a good disk.

Last ditch effort is to use dd to try to write zeros to each of those bad sectors to force the drive to reallocate them from the spare pool.  For each of those numbers, first try to read the sector:

```

sudo dd if=/dev/sdd bs=512 of=/dev/null skip=XXX count=1
```

This should fall with an IO error.  If it doesn't, something is wrong, so don't proceed with writing to the drive:

```
sudo dd if=/dev/zero bs=512 of=/dev/sdd count=1 seek=XXX
```

If that succeeds, then either the sector turned out to be ok ( but its contents have been lost ), or the drive reallocated it from the spare pool.  Once you get through all of the bad sectors, check the smart numbers again and the pending count should be 0, but the reallocated count may have gone up.  If it did, then the drive is failing and you should replace it, if not, then the errors have been corrected ( though again, with data loss ).

Then you might be able to use testdisk to scan the drive and rebuilt your lost partition table, then fsck the filesystem and then you can try to mount it, and then you can try to figure out why you didn't have a working raid1.

---

### Post by macdalor on 2011-08-16
Here is what I got for both commands:

> dd: invalid number `XXX'I guess this is "game over" then from what you're saying?

---

