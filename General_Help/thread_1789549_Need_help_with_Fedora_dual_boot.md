---
title: "Need help with Fedora dual boot"
date: 2011-06-23
forum: General Help
---

### Post by Easy Limits on 2011-06-23
I installed Fedora 15 next to my Ubuntu 10.04 partition and now I can't boot in to Ubuntu, just Fedora.  I tried sudo update-grub with the Ubuntu live cd and nothing.  The Fedora grub menu just shows Fedora and "other".  When I select "other" I just get a blinking cursor.  Any suggestions?

---

### Post by wildmanne39 on 2011-06-24
> **Easy Limits said:**
> I installed Fedora 15 next to my Ubuntu 10.04 partition and now I can't boot in to Ubuntu, just Fedora.  I tried sudo update-grub with the Ubuntu live cd and nothing.  The Fedora grub menu just shows Fedora and "other".  When I select "other" I just get a blinking cursor.  Any suggestions?Hi, did you chroot into the partitions from the livecd? 
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by Easy Limits on 2011-06-24
Thanks for the response!  When I get a chance I will try out your suggestion.

---

### Post by idoitprone on 2011-06-24
> **Easy Limits said:**
> Thanks for the response!  When I get a chance I will try out your suggestion.

there two ways to tackle this problem

add ubuntu to fedora
or

chroot
or reinstall grub2
[https://help.ubuntu.com/community/Grub2#Copy LiveCD Files](https://help.ubuntu.com/community/Grub2#Copy LiveCD Files)

chroot is the longest and most complicated. fedora is simplist



fedora override your mbr. so you can add ubuntu to fedora.
[http://www.gnu.org/software/grub/manual/legacy/grub.html#Top](http://www.gnu.org/software/grub/manual/legacy/grub.html#Top)

---

### Post by Easy Limits on 2011-06-24
Well, the chroot suggestion didn't work out.  I couldn't mount my Ubuntu partition.  

I am going to do a reformat and start over just to see where I went wrong.  Learn, learn, learn.8-)

---

### Post by -kg- on 2011-06-24
If you want to retain control of the MBR in your original installation (in this case, Ubuntu), you need to opt to install the GRUB boot loader of the second installation (in your case, Fedora) in the partition in which it resides instead of the default location (the MBR).  This leaves the original boot loader in the MBR.

Once you've installed Fedora, with its boot loader in it's partition, boot into Ubuntu and run "sudo update-grub" in the terminal.  GRUB will auto-detect Fedora and include it in Ubuntu's GRUB menu.

Of course, simplest for you (if you're going to reinstall everything) would be to install Fedora first, then Ubuntu second.  I don't know whether Fedora has ever corrected it (surely they have by now?!), but for quite a while they were using a version of GRUB that wouldn't detect the boot directory if it was located on an ext4 partition...it had to be ext 3.  Since Ubuntu is ext4 by default....

---

### Post by Easy Limits on 2011-06-24
Thanks guys!  I appreciate your help/suggestions.

---

### Post by idoitprone on 2011-06-24
mount the ubuntu parition in fedora

i want the names of the files in /boot in ubuntu.

use nautilus to mount the partition.
go to the terminal

```
cd /media/<tab>/boot

```
assuming that is the only mounted partition
post the output of ls
```
ls
```
and 

```
blkid
```

while your at it post the output of
```
cat /boot/grub/menu.lst

```
i always forget distro differences
i am going to write an entry so you can boot ubuntu

---

