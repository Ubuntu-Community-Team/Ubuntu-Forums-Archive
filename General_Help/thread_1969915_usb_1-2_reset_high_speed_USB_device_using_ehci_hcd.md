---
title: "usb 1-2: reset high speed USB device using ehci_hcd and address *"
date: 2012-04-30
forum: General Help
---

### Post by nearlymagicman on 2012-04-30
I got a problem with my external 1TB usb harddrive truecrypt volume as it suddenly is not recognized anymore by the system.
I was moving some files around until it got really slow, from around 20MB/s down to a few kb/s, I then dismounted the device correctly. Plugged it out and when I tried to plug it back in, it was not recognized anymore.

The syslog shows:
```
Apr 30 23:35:39 innenminister kernel: [  880.570033] usb 1-2: new high speed USB device using ehci_hcd and address 3
Apr 30 23:35:39 innenminister kernel: [  880.732258] scsi9 : usb-storage 1-2:1.0
Apr 30 23:36:01 innenminister kernel: [  903.240033] usb 1-2: reset high speed USB device using ehci_hcd and address 3
```

And that resetmessages repeats around every 20 seconds.


fdisk -l shows:
```
  Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 endet nicht an einer Zylindergrenze.
/dev/sda2              13        8414    67481600    7  HPFS/NTFS
/dev/sda3            8415       24793   131560449    5  Erweiterte
/dev/sda5            8415       13278    39061504   83  Linux
/dev/sda6           13278       24219    87889920   83  Linux
/dev/sda7           24220       24793     4606976   82  Linux Swap / Solaris
```


I found that problem all over the [internet]("http://ubuntuforums.org/showthread.php?p=11523377"), but as there is no device listed I cannot change block size, or am I wrong?
I also did try whether windows recognize a usb device (even though it cannot cope with a truecrypt volume) but it fails as well.

So I wonder if the device is broken, which is quite unlikely as it is not even half a year old and been well treated, or if something got messed up badly but could be fixed.

---

