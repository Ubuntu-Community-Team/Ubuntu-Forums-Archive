---
title: "Grub 1.5 Error 22 - Partition Deleted on Netbook."
date: 2010-04-29
forum: General Help
---

### Post by lszanto on 2010-04-29
Ok so I originally had Windows XP and Ubuntu NBR installed on my netbook. I decided I didn't want to go with Ubuntu NBR so I just set to default grub to windows so I could worry about removing Ubuntu later.

I then installed Jolicloud(a netbook optimized version of ubuntu) through a windows xp installer and quite liked it, so much so that I quickly fired up gparted and removed the ubuntu partition.

The issue now is I can't get the computer to boot, full stop.

I just run into the error:

"Grub 1.5

Error 22"

I know this is because I have removed the partition, is there any way I can restore the mbr for my windows partition?

I have a usb which I have tried running: Freedos, Windows 98 boot cd, super grub disk.

But have had no success in fixing my mbr.

Any ideas or help would be greatly appreciated asap for university.

Thanks in advance, lszanto

P.s I wasn't exactly sure where to put this sorry, so sorry if it's in the wrong section.

---

### Post by dino99 on 2010-04-29
grub 1.5 ?

the actual grub release is 1.98

from which distro have you got that grub ?

so you still have xp but cant boot on it because you overwrite its bootloader when installing ubuntu, now you have to reinstall with fixmbr from xp cd

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by lszanto on 2010-04-29
Ah sorry my bad, I think it may have been stage 1.5? It sounds more correct to me anyways.

Um to my knowledge grub installed from ubuntu netbook remix, as it crashed when I removed the partition netbook remix was installed on.

I used the Jolicloud windows installer which installs from inside windows/I think it somehow embeds itself with windows? I'm not 100% sure but I don't think that is the issue.

I would use fixmbr from the cd but I don't have a usb cd drive, I've tried to find some sort of windows xp rescue cd that I can install on usb but have had no luck.

---

### Post by dino99 on 2010-04-29
better to trust ubuntu to install ubuntu rather than crozoff  :P

on my end i only use ubuntu, no more windoz, no more need it. Wine take care of my oldish windoz apps :P

---

### Post by oldfred on 2010-04-29
You can install a generic windows boot loader to the MBR from Ubuntu liveCD.

sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

Actually for XP and before any windows boot disk uses the same code in the MBR. Vista & 7 are different but the above seems to work for all.

---

### Post by lszanto on 2010-04-29
Thank you sir, I now have Ubuntu installed, I may try and install WinXp/7 later. I wouldn't use it but I sorta need it for uni.

---

