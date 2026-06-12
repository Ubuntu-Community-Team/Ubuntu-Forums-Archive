---
title: "CD/DVD drive won't mount after upgrade to lucid"
date: 2010-06-14
forum: General Help
---

### Post by genfinch on 2010-06-14
I'm running ubuntu Lucid Lynx on an asus K50IJ series laptop. I'd had jaunty before and made a fresh install of lucid. My CD drive had been fine in jaunty, but doesn't mount any more in lucid. I have found numerous threads with promising-looking titles, but they either do not match my problem or their solutions don't work for me.
 
This is my situation:
The disc will turn for a bit after inserting, then stop. During that, the little light on the drive will flash a few times, then wink out. So I guess the power supply's fine. 

Output of ls -l /dev/{cd,dvd}*
```
lrwxrwxrwx 1 root root 3 2010-06-14 18:02 /dev/cdrom1 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-14 18:02 /dev/cdrw1 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-14 18:02 /dev/dvd1 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-14 18:02 /dev/dvdrw1 -> sr0
```

Output of sudo hdparm -I /dev/sr0
```
/dev/sr0:

ATAPI CD-ROM, with removable media
	Model Number:       HL-DT-STDVDRAM GT10N                    
	Serial Number:      
	Firmware Revision:  1.00    
	Transport:          Serial; Revision: 0x5356
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
```

**eject /dev/sr0** works fine.

BUT: The CD or DVD just won't show up on the desktop (and yes, I have the displaying of volumes on desktop enabled) or in the sidebar in nautilus and **/media/cdrom** or similar does not manifest itself. 

sudo mount /dev/sr0 gives me ```
mount: Couldn't find /dev/sr0 in /etc/fstab or /etc/mtab
```
finden
I have tried mkdir'ing the **/media/cdrom** and then adding the drive first to the fstab and then to the mtab with 
```
/dev/sr0 /media/cdrom udf,iso9660 user,noauto,exec,utf8 0 0
```
after which sudo mount /dev/sr0 /media/cdrom gave me 
```
umount: /dev/sr0: unknown device
```

The drive shows up in nautilus in **computer:///**, but clicking or double-clicking it or right-click --> open does nothing. 

I have installed **halevt**, no joy. 

If anyone can help me or point out a heplful thread that I haven't found yet, please please please let me know. Thanks!

---

### Post by genfinch on 2010-06-16
*bump*

---

### Post by king.knut on 2010-06-20
Did you find a solution for your problem? I'm desperately looking for one too. 

My situation is similar to yours. Just made a fresh install of Kubuntu Lucid Lynx on my new notebook, an Acer Timeline 4810TZG-414G50MN, and can't get the DVD-RW working. Starting from Live-CD everything worked fine. The mounted CD was shown in the "Device Notifier" and system installation worked like a charm. But after reboot neither data CD's nor music CD's nor DVD's got mounted or played.

I couldn't find any line in fstab mentioning the DVD-RW device nor a respective mountpoint in /media (both didn't exist when system was booted from Live-CD either). In /dev there is a block device called sr0 which is linked to scd0, cdrom, cdrw, dvd and dvdrw.

Following the instruction found in other threads I added following line to my fstab

```
/dev/scd0 /media/cdrom auto user,noauto,exec 0 0
```

and created the mountpoint /media/cdrom. But that didn't help.


Wheras k3b recognises the DVD-RW drive properly

```
knut@knut:~$ hdparm -I /dev/sr0
```

gives following error message

```

/dev/sr0:
HDIO_DRIVE_CMD(identity) failed: Bad address
```

or hangs.

Interesting is, that CD's and DVD's are mounted when in the drive at boot time. I even can eject them and put in another one once or twice which will be mounted then. But this only works two or three times at the most and then we are back at the afore mentioned behaviour.

Does all this make sense to anybody? Is this confusing behaviour due to some misconfiguration, a bug or even a hardware failure?

---

### Post by giddyup306 on 2010-06-20
I'm not an Ubuntu guru (hey that rhymes), but I had a similar problem when I switched to Lucid.  It had something to do with BIOS (if I remember right it was disabled in BIOS).  The thing is that I had to replace the drive (the old one was dead for quite some time), and after doing so it wouldn't mount. Since I'm not 100% sure if the drive would have worked in Jaunty, you can take this post at face value.

---

### Post by king.knut on 2010-06-22
Thanks giddyup306. You made my day. I switched in BIOS SATA-Mode to IDE and the drive works like a charm.

---

### Post by genfinch on 2010-07-04
I've tried the BIOS thing, but the SATA Configuration Settings only have "Enhanced" or "Compatible". Tried both, neither works. Anyone? Please...

---

### Post by giddyup306 on 2010-07-04
> **king.knut said:**
> Thanks giddyup306. You made my day. I switched  in BIOS SATA-Mode to IDE and the drive works like a charm.

No problem.  I like to try and help when I can.  ;)

> **genfinch said:**
> I've tried the BIOS thing, but the SATA Configuration Settings only have "Enhanced" or "Compatible". Tried both, neither works. Anyone? Please...

Yesterday when I updated Lucid, I saw that Brasero had several updates.  I think there is a software issue involved as well.  Ubuntu won't do an automatic update unless there is a security update available.  To do it manually go to system > administration > update manager.

---

