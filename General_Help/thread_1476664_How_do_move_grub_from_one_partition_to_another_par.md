---
title: "How do move grub from one partition to another partition"
date: 2010-05-08
forum: General Help
---

### Post by ozguitarplayer on 2010-05-08
Hi 
I don't know if this is possible however would like to know how to move grub from one partition to another. I may not have explainded that very well.....
I have a computer that i use to checkout different linux distros, however since the introduction of grub2 things have become difficult.
I have a number of primary partitions on the one hdd
If I install a o/s that uses grub on a partition and another partition  has a o/s that uses grub2 then on startup the o/s with grub2 no longer appears on the grub start up screen so I cannot boot into the grub2 o/s.
The reverse is ok i.e. if I install a grub2 o/s after a grub o/s all appear on the grub start up screen.

This leaves me in the situation where I have to always reinstall a grub2 o/s after i install a grub o/s. Hope that makes sense!!

This is why it would be easier (I hope) to be able to move grub from one o/s to another. 
I must admit I don't really understand it all that well and I know that mbr plays a role in it, however I think it's correct that the mbr can remain on an o/s yet grub is on another?

wishing and hoping....

---

### Post by nikhilbhardwaj on 2010-05-08
it should be possible
but in my opinion what you really need to do is
when you install your testing distros don't install their bootloaders
just enter a grub2 entry for them
that'd make a lot more sense

---

### Post by ozguitarplayer on 2010-05-08
Thanks,
However I thaik that since 09.10 there is no longer the option not to install grub at least not that I've noticed, it happens by default, although Debian Squeeze (testing) 
still offers it. 
You're right though it would have to be easier.

---

### Post by Luftfuß on 2010-05-08
Is you go into synaptic package manager (System->Administration->Synaptic Package Manager) and reinstall grub the grub install menu should let you pick the partition you want to install grub on. Search for grub, grub-pc should be the version installed (this is the newest grub) but if old grub is installed it should still work.

---

### Post by john newbuntu on 2010-05-08
What I would do is to backup the MBR into a file on an external USB drive. 
dd if=/dev/sda of=/media/myusb-whatever/boot.mbr bs=446 count=1
Just boot to any of your linux installations and restore it from the file.
dd if=/media/myusb-whatever/boot.mbr of=/dev/sda bs=446 count=1

_WARNING: Please read up on "dd" command in linux.  They can be destructive if used improperly._

If you use windows, you can download and use a simple tool called "MBRWiz" that does the same.

This way, you can install just about any distro and restore the one that you like on the MBR.  Of course, if you use grub2, please remember to run "sudo update-grub" or "sudo update-grub2" from your main install.  This way, it picks up all other new OS's.

---

