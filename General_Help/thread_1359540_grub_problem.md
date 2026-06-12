---
title: "grub problem"
date: 2009-12-19
forum: General Help
---

### Post by wp95 on 2009-12-19
hi, I recently installed ubuntu 9.10 on a new partition on a disk with windows 7 on the other partition. I ended up removing ubuntu by deleting its partition in windows, but when i start the computer now I get the messages..
"Grub loading
error: no such disk
grub rescue>"
the only thing I could think to try was the repair option with the windows 7 DVD which didn't work. It seems ubuntu has automatically overwritten the windows boot sequence which seems pretty mean to me! I can't use the computer at all now so any help would be much appreciated.

---

### Post by Darael on 2009-12-19
Well, you have a couple of options. You'll want to find out how to reinstall the Win7 boot loader (I'm afraid I don't know) but you can probably get Windows to load by typing the following at the grub rescue prompt:
```
insmod ntfs
set root=(hd0,0)
drivemap -s (hd0) ${root}
chainloader +1
boot
```

---

### Post by Leppie on 2009-12-19
i found [this howto]("http://www.ehow.com/how_4836283_repair-mbr-windows.html") to restore the mbr with the win7 dvd.

---

### Post by drs305 on 2009-12-19
Here is another link which you might want as you restore things:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

When you deleted the partition, you removed the folder which GRUB 2 looks for during boot. (GRUB 2 was still on the MBR and was controlling things. When it couldn't find grub.cfg, it generated the error message and reverted to the rescue prompt to allow you to try to restore the system. Since you no longer have a linux partition, restore the Windows bootloader per the instructions in any of the links provided in this thread.

---

### Post by wp95 on 2009-12-19
thankyou! in case anyone else has the same problem, the link [drs305]("http://ubuntuforums.org/member.php?u=223945") provided had the info that ended up working. 
by the way this was such good fast help I think its given me the confidence to try ubuntu again.

---

### Post by drs305 on 2009-12-19
> **wp95 said:**
> thankyou! in case anyone else has the same problem, the link [drs305]("http://ubuntuforums.org/member.php?u=223945") provided had the info that ended up working. 
by the way this was such good fast help I think its given me the confidence to try ubuntu again.

Welcome to Ubuntu and the Ubuntu forums. There will always be people around willing to help.

By the way, you can mark a thread SOLVED via the Thread Tools link at the top right of the original post. Marking it solved shows other users threads which contain at least an answer for the original poster, as well as letting the 'helpers' concentrate on unresolved issues.

---

### Post by Leppie on 2009-12-19
> **wp95 said:**
> thankyou! in case anyone else has the same problem, the link [drs305]("http://ubuntuforums.org/member.php?u=223945") provided had the info that ended up working. 
by the way this was such good fast help I think its given me the confidence to try ubuntu again.

thank you for indicating what worked for you, this could help many others :)

and give ubuntu another try, it's really not so bad ;)

---

