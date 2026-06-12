---
title: "GRUB Boot Menu Error"
date: 2009-09-18
forum: General Help
---

### Post by fatigue on 2009-09-18
When trying to get into QGRUBEditor, a popup window appeared saying that it wasn`t able to read/write access to one of these files:

/boot/grub/menu.lst
/boot/grub/device.map
/etc/mtab

Since this popped up, I haven`t been able to load up my operating systems. I currently dual-boot XP and Ubuntu 8.04 and instead of getting the boot screen, I get GRUB. I`ve tried to remake my boot screen by trying the code below:

```
sudo grub
find /boot/grub/stage1
root (hd*,*)
setup (hd0)
quit
```
It recognizes where stage1 is located and the setup is `successful`, but when I try to restart my computer, nothing changes. Is there a way that I can manually bring back my boot menu?

---

### Post by Sef on 2009-09-18
I would use another computer and download [Super GRUB Disk]("http://supergrubdisk.org/").  That will easily reinstall GRUB.

---

### Post by fatigue on 2009-09-18
I have super GRUB disk.
Could you give me command for reinstall grub?
also does this delete xp/linux partition?
Thank you

---

### Post by cholericfun on 2009-09-18
check this out:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

especially the part (quote):

"6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)"."

also check menu.lst what partitions are actually pointed to
i once had the problem that grub mysteriously wrote the wrong partition number in menu.lst (i.e. (sda4 for 4th part. instead of sda3)

---

### Post by fatigue on 2009-09-19
hd(0,3) didnt work, 
I managed to boot from super grub disk but how can I reinstall grub without deleting linux and xp? Could anyone give me command?

---

### Post by fatigue on 2009-09-19
please , could anyone help me about this?:confused:

---

### Post by cholericfun on 2009-09-19
> **fatigue said:**
> hd(0,3) didnt work, 
I managed to boot from super grub disk but how can I reinstall grub without deleting linux and xp? Could anyone give me command?



here, look, YOUR partition is prob not hd(0,3)

it is whatever grub told you it is ...
also it is not sd (*,*) from your first post
cause you need to insert something into those *,*

forget supergrub, or reed up on it.

just go back to your LiveCD, and go through those grub commands again.
in my opinion, thats the easyest.

good luck

---

### Post by AmerNewbieInDE on 2009-09-19
i just got done redoing my grub because i copied everything to a new hd. boot with live cd, open terminal, sudo grub, find /boot/grub/stage1. mine was (hd1,0) but change it to what ever yours shows, type root (hd1,0) pointing to your linux root. then setup (hd0). this sets up grub on the mbr of the first disk. it worked for me, but i see you are also puting the ( ) in the wrong place, not hd(0,3) but (hd0,3)

---

### Post by fatigue on 2009-09-20
Solved!

Basically, I boot ubuntu with Super Grub Disk.
Once I booted ubuntu, I install start-up manager.
Start-up manager re-generate grub if your grub is missing.

Thank you for helping. I appriciate it

---

