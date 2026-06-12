---
title: "iPod mounting issue"
date: 2011-05-14
forum: General Help
---

### Post by quarterkraut on 2011-05-14
Hello everybody. I use my iPod Video 5.5 gen as a external hard drive just to put some important files on. When 11.04 came out I uninstalled my wubi which was 10.10 and did a fresh install of 11.04. When I logged in I simply copied my files from the iPod Video to my hard drive without any issues. Now about two weeks later however, Ubuntu will not recognize my iPod Video when I plug it in. The iPod will charge, but not mount. What really confuses me is that my iPod Touch will mount just fine, and I can even sync music to it using Banshee. Ubuntu also recognizes my Kindle and any SD card or flash drive I throw at it. Has anyone else had any problems like this or is it just me? Any thoughts on how to continue?

---

### Post by barkhat on 2011-05-16
I'm having a similar-type issue. All of a sudden I am getting the following message when I plug in my Ipod:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdf2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I am using Natty and I don't know why this is suddenly happening. I've played this one previously. I'm seeking guidance, advice, help, etc.  Hoping some knowledgeable ones can help us solve this problem.

Thank you.

---

### Post by barkhat on 2011-05-20
> **quarterkraut said:**
> Hello everybody. I use my iPod Video 5.5 gen as a external hard drive just to put some important files on. When 11.04 came out I uninstalled my wubi which was 10.10 and did a fresh install of 11.04. When I logged in I simply copied my files from the iPod Video to my hard drive without any issues. Now about two weeks later however, Ubuntu will not recognize my iPod Video when I plug it in. The iPod will charge, but not mount. What really confuses me is that my iPod Touch will mount just fine, and I can even sync music to it using Banshee. Ubuntu also recognizes my Kindle and any SD card or flash drive I throw at it. Has anyone else had any problems like this or is it just me? Any thoughts on how to continue?

Have you figured out any solutions for this problem, yet?

---

### Post by barkhat on 2011-05-25
bump

---

### Post by armoftheland on 2011-05-28
i third this issue using natty

---

### Post by barkhat on 2011-05-31
Not sure why there is no response to this thread. I've been unable to find any information elsewhere in search so I hold out hope that someone can address this.

---

### Post by shantiq on 2011-06-06
same here on natty anyone knows?   this message appears when pluging ipod in


```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdf2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


i do not understand this message:KS   try dmesg   what is this?

---

### Post by deckoff on 2011-06-20
Really, no answer? It seems natty does not mount correctly my ipod anymore - the only software to work with it is floola 6.1, though the newer version 2011 will not work, too ??? weird... Any info on this

---

### Post by gizmo720 on 2011-06-20
open your terminal and type:
```
sudo fdisk -l
```
and
```
 dmesg | tail
```

post the outputs

---

### Post by JohnReid on 2011-07-07
I have the same problem. sudo fdisk -l:

> Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000543f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      180996  1453850338+  83  Linux
/dev/sda2          180997      182401    11285662+   5  Extended
/dev/sda5          180997      182401    11285631   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 159.8 GB, 159840301056 bytes
26 heads, 50 sectors/track, 30018 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30019   156093788    b  W95 FAT32
Partition 1 does not start on physical sector boundary.



end of dmesg:
> [   72.806578] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   90.594183] usb 1-1.3: new high speed USB device using ehci_hcd and address 3
[   90.624676] hub 1-1:1.0: unable to enumerate USB device on port 3
[   90.994228] usb 1-1.3: new full speed USB device using ehci_hcd and address 4
[   91.154236] usb 1-1.3: new high speed USB device using ehci_hcd and address 5
[   91.361863] usbcore: registered new interface driver uas
[   91.391149] Initializing USB Mass Storage driver...
[   91.391233] scsi6 : usb-storage 1-1.3:1.0
[   91.391336] usbcore: registered new interface driver usb-storage
[   91.391338] USB Mass Storage support registered.
[   92.296328] usb 1-1.3: USB disconnect, address 5
[   92.474635] hub 1-1:1.0: unable to enumerate USB device on port 3
[   92.784395] usb 1-1.3: new full speed USB device using ehci_hcd and address 7
[   92.944282] usb 1-1.3: new high speed USB device using ehci_hcd and address 8
[   92.974658] hub 1-1:1.0: unable to enumerate USB device on port 3
[   93.214316] usb 1-1.3: new high speed USB device using ehci_hcd and address 9
[   93.333493] scsi7 : usb-storage 1-1.3:1.0
[   94.332438] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   94.333214] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   94.337026] sd 7:0:0:0: [sdb] Spinning up disk....ready
[  100.725913] sd 7:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[  100.726671] sd 7:0:0:0: [sdb] Write Protect is off
[  100.726677] sd 7:0:0:0: [sdb] Mode Sense: 68 00 00 08
[  100.728174] sd 7:0:0:0: [sdb] No Caching mode page present
[  100.728180] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  100.729678] sd 7:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[  100.731900] sd 7:0:0:0: [sdb] No Caching mode page present
[  100.731906] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  100.915852]  sdb: sdb1
[  100.917409] sd 7:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[  100.919386] sd 7:0:0:0: [sdb] No Caching mode page present
[  100.919389] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  100.919391] sd 7:0:0:0: [sdb] Attached SCSI removable disk


Any advice?

Thanks,
John.

---

### Post by sixela295 on 2011-07-07
Bump. Same issue here.

---

### Post by ktec on 2011-08-10
Same problem here, using Natty and 80gb Ipod - have just restored the ipod using my friends Mac and now I get this message.

---

