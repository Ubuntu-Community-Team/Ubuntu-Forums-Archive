---
title: "Calling all Grub Gurus"
date: 2006-05-01
forum: General Help
---

### Post by bpont on 2006-05-01
I'm close to swapping out my second hard drive for a larger one next week.  The second hard drive has Ubuntu on it, the first drive has Windoze.  Grub is installed on the first hard drive, but /boot/grub/menu.1st is on the second drive.  So, I'm thinking that if something goes wrong with installing the new second hard drive, I won't be able to boot into either drive unless I hack at the grub command line, which I'd like to avoid.

My question is, how do I move my menu.1st file onto my first hard drive and configure grub to find it, so that it doesn't touch my second hard drive at all during boot up (unless I boot into Ubuntu)?  I just want to do this as a precaution until the new second hard drive is up and running and I've completed a fresh install of Dapper when it comes out (hopefully) next month.  Thanks.

---

### Post by geek.de.nz on 2006-05-02
I'm not sure if grub can handle vfat (fat32). If yes, you could just put it on a vfat partition on your first hd, or if you have space left, create a small (50-100MB) /boot partition on the first hd and copy the /boot/grub directory there. Then you can later also put your kernels on there.

Once you got that sorted, just follow 
[http://gentoo-wiki.com/HOWTO_Quick_GRUB](http://gentoo-wiki.com/HOWTO_Quick_GRUB) . Should be easy enough. (hdX,Y) is just like /dev/hd(X+1)(Y+1), (X+1) a letter. Hope you understand what I mean, otherwise it should be explained in the HOWTO.

Otherwise. If you're replacing the old hd anyway, you could just copy over all your partitions from your old drive (e.g. dd if=/dev/hdc of=/dev/hdb) and you should still be able to boot your old OS. Then you can install the new OS. dd is really a nice tool. ;-)

---

### Post by bpont on 2006-05-05
I guess what I'm asking is if I disconnect my second hard drive and boot up my computer, what will happen?  The menu.1st file resides on my second (disconnected) hard drive.  Will grub boot at all?  Can I at least work from the grub command line?

---

