---
title: "Corrupted both my fat32 USB AGAIN"
date: 2010-12-30
forum: General Help
---

### Post by amsterdamharu on 2010-12-30
[solution]
[COLOR=Red]When I got the cannot write to read only filesystem error I unmounted it with sudo (nautilus has no unmount option).
To do so I pressed alt + F2, typed gnome-terminal and clicked run then typed the following command:
```
sudo umount /media/(pressed tab)
```
Then just click on it in nautilus and its mounted as writable.
The reason for this might be because I used it as a bootable tinycore drive and sometimes gets unmounted wrong or something like that.
[/COLOR][/solution]

So I try to copy some files from one machine to another and plugged in my 2GB memory stick. Upon trying to copy the files it says "cannot write to read only filesystem" and no way I could get it to write to it. 
Savely remove drive a couple of times and re plugged in but no show, took it to the other computer but same deal.
Plugged in another USB stick I got and created a directory, when I try to write to it I get an IO error trying to copy the files to there.
dmesg | tail
Gives me "FAT: Corrupted directory", usually I just reformat the drive and start over again but this time I am fed up, 2 drives in 10 minutes time? That's a bit too much for an OS everyone claims to be so stable. 

My question is; what breaks the drives every time and what can I do about it. This only happens when using them in Ubuntu. After using them for months in Windows there is no problem at all but using them a couple of times in Ubuntu will guarantee problems like these.

---

### Post by dcstar on 2010-12-30
> **amsterdamharu said:**
> So I try to copy some files from one machine to another and plugged in my 2GB memory stick. Upon trying to copy the files it says "cannot write to read only filesystem" and no way I could get it to write to it. 
**Savely remove drive a couple of time**s and re plugged in but no show, took it to the other computer but same deal.
..........

Do you actually **wait** for the write cache to empty before pulling out the USB?

---

### Post by amsterdamharu on 2010-12-30
Hi dcstar, thank you for your reply.

The handy thing about it is that nautilus never tells you when it's actually finished so I wait for the light to turn off and pull it.

Not that that seems to matter much, just reformatted the whole drive in Windows and used unetbootin to make it bootable and yes after using it in Ubuntu 3 times it's mounted as read only again.

This is the output of dmesg | tail
dmesg | tail
```
[  455.026637] scsi 7:0:0:0: Direct-Access     Ut165    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[  455.037207] sd 7:0:0:0: Attached scsi generic sg1 type 0
[  455.050011] sd 7:0:0:0: [sdb] 3948544 512-byte logical blocks: (2.02 GB/1.88 GiB)
[  455.050896] sd 7:0:0:0: [sdb] Write Protect is off
[  455.050908] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  455.050917] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  455.057799] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  455.057814]  sdb: sdb1
[  455.320922] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  455.320947] sd 7:0:0:0: [sdb] Attached SCSI removable disk

```

Now that I safely remove and unplug replug it works ok again. I just remembered even with redhat that Linux has this habbit of corrupting fat32 usb sticks or it's something that I do wrong but the strange thing is that I can use this USB for months in Windows without problems (I safely remove there too) but never seem to get it right in Linux.

---

### Post by amsterdamharu on 2011-01-01
See first post for solution.

---

