---
title: "I destroyed my grub."
date: 2009-07-09
forum: General Help
---

### Post by kogger on 2009-07-09
Okay, this all started because I was trying to install a graphical version of grub. Needless to say, it didn't work, and at the current moment I'm busy trying to at least restore what I had before. I have a dual-boot with windows, which I'm pretty sure got destroyed in the process, but in an attempt to save it I think I forced grub to only be able to try and boot into a now non-existent operating system.

So here's the current situation.

When I simply boot up my computer, I get an Error 17, so I can't do anything at all. When I boot into a live dvd (which sometimes has issues), I can see and mount two partitions, one for linux and one for files, so I know I still have everything, I just can't access it.

When I open up grub (sudo grub) and try to find stage 1 (find /boot/grub/stage1), I get an Error 15 (file not found). I've tried doing root(hdX,y) and setup(hdX) with every one of my partitions, and none of them can mount.

Any ideas on how I can get my computer working again?

---

### Post by mano cazalet on 2009-07-09
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

try the instructions of the second part of the first post, mounting your root partition from live cd

hope that helps

---

### Post by nacho32 on 2009-07-09
you could download the super grub boot loader [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) I've used this to automatically fix the grub a must have.

---

### Post by kogger on 2009-07-09
I've already looked through that, but no matter what I do I can't get it to find /boot/grub/stage1.

---

### Post by synapsys on 2009-07-09
> **nacho32 said:**
> you could download the super grub boot loader [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) i've used this to automatically fix the grub a must have.

+1

---

### Post by kogger on 2009-07-09
How do I use the super grub disk? Their website isn't very helpful.

---

### Post by nacho32 on 2009-07-09
> **kogger said:**
> How do I use the super grub disk? Their website isn't very helpful.

on the top right side you have a choice of what to download , I would suggest the cd, burn to disk make sure bios is set to boot off cd drive first and you set

---

### Post by kogger on 2009-07-09
Either I'm doing something wrong, or the disk isn't working. I keep getting Grub Error 17.

---

### Post by kogger on 2009-07-09
Okay, I think I've made a step in the right direction. I went to "boot partition," and after unhiding my linux partition (I used a hide command before to try and get Windows to work that I only now realized may have affected what I've been trying to do), I can again boot into linux, but it lists a whole bunch of text instead of just showing the ubuntu loading bar.

---

### Post by nacho32 on 2009-07-09
> **kogger said:**
> Either I'm doing something wrong, or the disk isn't working. I keep getting Grub Error 17.

try the disk on another pc, if it fails I would suggest to re-download re burn

---

### Post by kogger on 2009-07-09
The main thing I'm still confused about though is why would installing a different version of grub would erase Windows?

---

