---
title: "External NTFS drive disconnecting"
date: 2012-01-14
forum: General Help
---

### Post by ForcedFeed on 2012-01-14
I'm new to Linux, I've only been using Ubuntu for about two days but I really like it. I have an external USB HDD using NTFS. It was working out of the box with 11.10 but I couldn't write to it. I installed NTFS Configuration Tool and ran:
```
sudo mkdir -p /etc/hal/fdi/policy
```
It was added to fstab so I commented that out. 

```
#UUID=80303A72303A6EF2	/media/Storage	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
```

Now the drive is mounted normally when connected and I can write to it. The problem I have now is the drive keeps disconnecting and reconnecting. For example, if I play some music or video that is stored on the drive, it will play for about 1 minute and then disconnect/reconnect. Here is what the logs show:

```
Jan 14 10:35:41 DJ-Ubuntu kernel: [ 2021.952085] usb 2-4: new high speed USB device number 2 using ehci_hcd
Jan 14 10:35:41 DJ-Ubuntu kernel: [ 2022.087670] scsi5 : usb-storage 2-4:1.0
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.143334] scsi 5:0:0:0: Direct-Access     Generic  External         1.13 PQ: 0 ANSI: 4
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.143504] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.143743] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.144667] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.144868] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.148369] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.152855] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.153043] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.157520] scsi: killing requests for dead queue
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.158099] sd 5:0:0:0: Attached scsi generic sg3 type 0
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.161225] sd 5:0:0:0: [sdc] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.162716] sd 5:0:0:0: [sdc] Write Protect is off
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.162725] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.166465] sd 5:0:0:0: [sdc] No Caching mode page present
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.166475] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.170180] sd 5:0:0:0: [sdc] No Caching mode page present
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.170192] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.179439]  sdc: sdc1
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.183195] sd 5:0:0:0: [sdc] No Caching mode page present
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.183207] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Jan 14 10:35:42 DJ-Ubuntu kernel: [ 2023.183215] sd 5:0:0:0: [sdc] Attached SCSI disk
Jan 14 10:43:21 DJ-Ubuntu kernel: [ 2482.052806] usb 2-4: USB disconnect, device number 2
Jan 14 10:43:21 DJ-Ubuntu kernel: [ 2482.112822] scsi: killing requests for dead queue
Jan 14 10:43:21 DJ-Ubuntu kernel: [ 2482.356097] usb 2-4: new high speed USB device number 3 using ehci_hcd
Jan 14 10:43:21 DJ-Ubuntu kernel: [ 2482.494162] scsi6 : usb-storage 2-4:1.0
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.496364] scsi 6:0:0:0: Direct-Access     Generic  External         1.13 PQ: 0 ANSI: 4
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.496472] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.516291] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.536286] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.560286] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.580268] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.596275] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.616268] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.632285] scsi: killing requests for dead queue
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.648549] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.654805] sd 6:0:0:0: [sdd] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.656163] sd 6:0:0:0: [sdd] Write Protect is off
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.656171] sd 6:0:0:0: [sdd] Mode Sense: 23 00 00 00
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.658300] sd 6:0:0:0: [sdd] No Caching mode page present
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.658307] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.661161] sd 6:0:0:0: [sdd] No Caching mode page present
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.661169] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.670579]  sdd: sdd1
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.674144] sd 6:0:0:0: [sdd] No Caching mode page present
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.674153] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Jan 14 10:43:22 DJ-Ubuntu kernel: [ 2483.674157] sd 6:0:0:0: [sdd] Attached SCSI disk
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203641] quiet_error: 27 callbacks suppressed
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203649] Buffer I/O error on device sdc1, logical block 9834741
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203658] Buffer I/O error on device sdc1, logical block 9834742
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203663] Buffer I/O error on device sdc1, logical block 9834743
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203668] Buffer I/O error on device sdc1, logical block 9834744
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203673] Buffer I/O error on device sdc1, logical block 9834745
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203678] Buffer I/O error on device sdc1, logical block 9834746
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203683] Buffer I/O error on device sdc1, logical block 9834747
Jan 14 10:43:23 DJ-Ubuntu kernel: [ 2484.203688] Buffer I/O error on device sdc1, logical block 9834748
```

I don't have any issues at all with the drive in Win7. Any help is appreciated, thanks!

---

### Post by ForcedFeed on 2012-01-15
Upgraded libatasmart to libatasmart4 0.18-1ubuntu2 and now I can no longer reproduce the issue. :D

---

