---
title: "Deleted Ubuntu partition and sent to grub rescue prompt PLEASE HELP"
date: 2011-01-13
forum: General Help
---

### Post by ingrown.potato on 2011-01-13
I dual boot windows xp and ubuntu 9.10. I wanted to uninstall ubuntu for another distro (musix). I was told to go windows partition manager and remove the ubuntu partition. After I did so I rebooted and instanlly taken to a commnd line which says:
 
GRUB loading
 error: no such partition
 
grub rescue > 
 
 
---
 
I've been researching online for almost 2 hours and nothing I came across matches my senario. I also tried to put in the windows cd but it goes to the command line first. I went into my BIOS and put "usb cd" on the highest priority and still nothing. PLEASE HELP!
 
Thanks in advance!

---

### Post by Quackers on 2011-01-13
You should either repair the mbr with a Windows XP repair disc, or install your other OS and let that deal with booting (assuming musix has grub or similar).

---

### Post by ingrown.potato on 2011-01-13
> **Quackers said:**
> You should either repair the mbr with a Windows XP repair disc, or install your other OS and let that deal with booting (assuming musix has grub or similar).
 
I can't boot from a cd, it takes me to the rescue prompt before I have a chance to boot from a cd. I tried to boot from a partitionmagic, and my windows xp cd.

---

### Post by Quackers on 2011-01-13
Then one of two things is happening. Either your boot device priority is not set to boot from cd first (in the bios) or the XP disc is not bootable, or faulty.

---

### Post by ingrown.potato on 2011-01-13
> **Quackers said:**
> Then one of two things is happening. Either your boot device priority is not set to boot from cd first (in the bios) or the XP disc is not bootable, or faulty.
 
I've tried to set the priority multiple times (and clicked save and exit) but it just reverts to the default settings.
 
Here are the default boot priority orders:
 
1:: SATA 
2:: IDE 1
3:: IDE 0
4:: PCI BEV
5:: USB HDD
6:: USB RDROM
7:: USB FDD
8:: USB KEY
 
---
 
I tried to put USBCDROM as the top priority but it wont stay that way.

---

### Post by Quackers on 2011-01-13
Is it a usb cd drive? Or is it on an IDE channel?

---

### Post by ingrown.potato on 2011-01-13
> **Quackers said:**
> Is it a usb cd drive? Or is it on an IDE channel?
 
I'm not sure what an IDE channel is, but its a regular intergrated laptop cd drive.

---

### Post by Quackers on 2011-01-13
Definitely not usb then :-)
Try IDE 1 first. If no good try IDE 0, or the other way round if you fancy :-)
Although I would have expected it to say cdrom really.

---

### Post by ingrown.potato on 2011-01-13
> **Quackers said:**
> Definitely not usb then :-)
Try IDE 1 first. If no good try IDE 0, or the other way round if you fancy :-)
Although I would have expected it to say cdrom really.
 
 
Some text appeared saying:
 
Inter UNDI PXE- 2.0 (build 082)
 
for realtek rtl... ----fast ethernet controller
 
client mac addr 
 
pxe-m0f: exeting pxe rom
 
---
 
not sure that that stuff means, and my disk did'nt load.

---

### Post by Quackers on 2011-01-13
Did that happen for both IDE entries?

---

### Post by ingrown.potato on 2011-01-13
> **Quackers said:**
> Did that happen for both IDE entries?
 
Yes but i toyed with it and am now able to boot my windows xp cd. Would it be better to load the windows cd? Or the ubuntu cd to fix grub, then do a proper uninstall.

---

### Post by Quackers on 2011-01-13
It's been a long time since I used XP. I think it's enough to enter the recovery console and choose the command prompt then enter fixmbr.
Maybe somebody else could confirm that?
Are you going to re-install Ubuntu, or a different OS?

---

### Post by ingrown.potato on 2011-01-13
I'm gonna go with musix, do you think it would be ok if I just installed that?
I didint safely uninstall ubuntu, I just deleted the partition in windows and thusly got that grub command thing

---

### Post by Quackers on 2011-01-13
I am unfamiliar with musix. Is it a complete operating system, with a bootloader, like grub?

---

### Post by ingrown.potato on 2011-01-13
I'm not sure how to check that, I guess I'll just use ubuntu studio instead.

---

### Post by ingrown.potato on 2011-01-13
Is there a way to just uninstall grub using the ubuntu live cd?
How could i do a "proper uninstall"

---

### Post by Quackers on 2011-01-13
You can use whichever system you would prefer! Just maybe do a little more digging with regard to Musix. In particular whether it uses grub legacy or grub2 or something else entirely.

---

### Post by Quackers on 2011-01-13
Grub will always be left. The only way (normally) to get grub out of the mbr is to over-write it with something else (like Windows for instance).

---

### Post by ingrown.potato on 2011-01-13
Or the new bootloader from musix?

---

### Post by Quackers on 2011-01-13
Hopefully, yes :-) But please bear in mind that support for Musix may be hard to find around here!

---

### Post by wilee-nilee on 2011-01-13
> **Quackers said:**
> It's been a long time since I used XP. I think it's enough to enter the recovery console and choose the command prompt then enter fixmbr.
Maybe somebody else could confirm that?
Are you going to re-install Ubuntu, or a different OS?

You are correct in the command and where.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

OP you might just fix the mbr, to boot to XP at this point while you find another OS to use.

---

### Post by gozzerd on 2011-01-15
To explain what happened. Grub in the MBR points to /boot/grub for the files needed to complete booting. The mbr is too small to hold all the needed stuff. When you deleted your partition, grub no longer had a way of finding /boot/grub. The mbr had no info about that partition anymore. Windows  keeps a back-up copy of the MBR, in the state it was in at the time of your windows install. Giving the fixmbr command copies that backup  into the mbr, overwriting grub. You would then have the same partition tables you had at Windows install. Probably just one big partition on the drive. So most likely you will have to re-partition your drive to create a space for musix.

---

