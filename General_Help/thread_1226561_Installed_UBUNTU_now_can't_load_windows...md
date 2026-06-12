---
title: "Installed UBUNTU now can't load windows.."
date: 2009-07-29
forum: General Help
---

### Post by chezzer on 2009-07-29
I installed ubuntu and divided it into a separte partition, I removed ubuntu partition through Vista and now i can't start Vista 

It says GRUB loader starting .... Error 17 ....
Please wait ...


***

nothing happens...
I attempted to reinstall ubuntu but the same happens when i restart the system

now i can only use ubuntu through the CD.
I can-t start windows

My Question > is there a way of removing this GRUB loader ?

---

### Post by lisati on 2009-07-29
> **chezzer said:**
> I installed ubuntu and divided it into a separte partition, [COLOR="Red"]I removed ubuntu partition through Vista[/COLOR] and now i can't start Vista 

It says GRUB loader starting .... Error 17 ....
Please wait ...


***

nothing happens...
I attempted to reinstall ubuntu but the same happens when i restart the system

now i can only use ubuntu through the CD.
I can-t start windows

My Question > is there a way of removing this GRUB loader ?

I think the problem could be that you removed ubuntu. (niggling thought: could you have removed Vista by accident?) If you want Ubuntu on your system, the easiest way of coping might be to reinstall ubuntu and let the installer take care of Grub. Otherwise you might need to dig out your Vista disk(s) and use that to repair your Vista installation.

---

### Post by zkriesse on 2009-07-29
It sounds like you messed up the hard drive partition...probably some files got messed up or moved around. What you should do now is stick in your original Vista OS disk(if you still have it of course...)and start from scratch. After you've done that, you should then be able to load Ubuntu on the system. If you do that though you should probably load Ubuntu on the whole partition...not just a piece of it...let me know if this helps you.

---

### Post by michy99 on 2009-07-29
You have to replace grub with the vista bootloader. Use the Vista recovery disk to restore the MBR.

---

### Post by philcamlin on 2009-07-29
> **michy99 said:**
> You have to replace grub with the vista bootloader. Use the Vista recovery disk to restore the MBR.

+1 then reinstall grub

---

### Post by zkriesse on 2009-07-29
like your sig dude....funny

---

### Post by hyperAura on 2009-07-29
well i think when the installer asked you where to install the grub u installed it on the windows partition and that replaced the vista bootloader.. well if u use the recovery disk be careful u might want to take ur disk out and use it as external hdd to grab some files u need in case somethin goes wrong and recovery disk cleans up ur files..

---

### Post by chezzer on 2009-07-29
Problem is the Windows CD restore doesn-t work .. but of course this is a windows problem and belongs to a different forum .. i just thought maybe i could remove GRUB through this version of ubuntu....

another thing, i can-t see my vista hd through ubuntu but i could before ??

---

### Post by merlinus on 2009-07-29
Open a terminal, and post results of

```
sudo fdisk -l
```

---

### Post by chezzer on 2009-07-30
OK ill do that later .. i am at work now ...

Thanks for all the responses by the way ! 

:D

---

### Post by chezzer on 2009-07-30
output from sudo fdisk -l 

........................................................



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cb91c44

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       88884   713959706    7  HPFS/NTFS
/dev/sda2           88885       91201    18611302+   5  Extended
/dev/sda5           91180       91201      176683+  82  Linux swap / Solaris
/dev/sda6           88885       91077    17615209+  83  Linux
/dev/sda7           91078       91179      819283+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

