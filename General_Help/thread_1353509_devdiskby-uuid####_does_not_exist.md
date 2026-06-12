---
title: "/dev/disk/by-uuid/#### does not exist"
date: 2009-12-12
forum: General Help
---

### Post by rheide on 2009-12-12
Ubuntu 9.10
2.6.31-16-generic
Acer Extensa 5620Z Laptop

I have been running Karmic Koala from a fresh install for the last several weeks with NO problems.

Tonight, I ran the update. While it was running, I locked my screen. I came back later and unlocked the screen and the update had completed and was waiting to reboot. I answered the prompt indicating that I would reboot later, closed all open screens, and then selected the Ubuntu menu reboot option. 

The boot-up got as far as displaying the Ubuntu circle, but no progress line. Eventually the screen went black.

I power off and when I turn the machine back on, I get the grub menu. If I select recovery mode, I see:

Gave up waiting for the root device. Common problems:
-Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)
ALERT! /dev/disk/by-uuid/##### does not exist. Dropping to a shell!

Using a 9.04 Live CD, I am able to use GParted to see that the UUID in the Alert matches the UUID for the sda1 partition information.

How do I correct this problem?

---

### Post by projectbronco on 2009-12-12
I am having a similar problem. Let's hope one of us gets if figured out. :)
[http://ubuntuforums.org/showthread.php?t=1353482]("http://ubuntuforums.org/showthread.php?t=1353482")

---

### Post by justin_guerin on 2009-12-12
> How do I correct this problem? 

Boot using the Ubuntu live CD, and check that your root file system is OK (run fsck on it).  

If that passes, mount it (and the partition that includes /boot, if separate) and chroot into that partition.  From the chroot, try rebuilding your kernel image.

If anything fails, post the error message.  If you don't manage to fix it, post everything you did, successful or not, so folks can know what you've already tried.

Justin

---

### Post by rheide on 2009-12-13
Justin,

I don't mind working in the command line, but I'm not certain that I know what I'm doing.

> **justin_guerin said:**
> Boot using the Ubuntu live CD, and check that your root file system is OK (run fsck on it).  


I executed:
  sudo fsck /dev/sda1

Results:
  fsck 1.41.4 (27-Jan-2009)
  e2fsck 1.41.4 (27-Jan-2009)
  /dev/sda1: clean, 187289/7143424 files, 9292172/28559545 blocks

> **justin_guerin said:**
> If that passes, mount it (and the partition that includes /boot, if separate) and chroot into that partition.  From the chroot, try rebuilding your kernel image.


I presume my fsck results pass. But, could you please detail the steps needed to rebuild the kernel image?

Thanks.

---

### Post by rheide on 2009-12-13
Maybe asking for details on how to recompile my kernel is asking a bit too much. I have browsed for directions to recompile the Karmic kernel, and everything I find seems to be using apt-get to bring in packages before starting to compile.

Maybe just some explaination of how using apt-get from a Live CD boot would be helpful. How will the downloaded packages end up on the hard drive?

Also, do you have any suggestions on the best set of directions on recompiling the Karmic kernel?

---

### Post by TBWTBW on 2009-12-13
Same problem here since yesterday's update.

---

### Post by justin_guerin on 2009-12-13
Hey.  Sorry, but real life is getting in my way here.

Anyway, what you'll want to do is this:
boot using your CD, using the "Try Ubuntu without any change to your computer" option
mount your hard disk somewhere.  You should be able to do this by opening Nautilus and clicking on the device icon.
Open a terminal window, and cd into the mounted directory.  Verify your files are there, and that you're in the directory that would be root (/) if you had booted from the hard disk.
If there's not a /proc directory, make one then mount is like this "sudo mount -t proc proc <path>/to/proc", where <path>/to/proc is the path to your mounted hard disk with /proc on the end.  That is, /media/hda1/proc or similar.
chroot into the new system "chroot /path/to/new/root"
from here, everything you do will be as if you were booted from your hard drive.  You really only need to rebuild your kernel image, so if you "dpkg-reconfigure <linux-image-2.6.31-14-generic" (or whatever is appropriate for your kernel image) that should do it.
Once the image is rebuilt, try rebooting.

If that doesn't fix your problem, you may need to make sure your file system driver is built into your kernel image.  Check that the module is specified in the image config.  I'm sorry I don't know where that is offhand, but if a Google search doesn't turn it up, write back and I'll investigate.

I'll send this now since I have to get going, but I will try to check in tomorrow.

Justin

---

### Post by rheide on 2009-12-13
Justin,

Yes, real life can get in the way...

I tried to follow your directions. I may have missed something, but below are the results from my terminal session:

```

ubuntu@ubuntu:~$ sudo mount -t proc proc /media/disk/proc
ubuntu@ubuntu:~$ cd /media/disk
ubuntu@ubuntu:/media/disk$ sudo chroot /media/disk
root@ubuntu:/# sudo dpkg-reconfigure linux-image-2.6.31.16-generic
sudo: unable to resolve host ubuntu
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
Package `linux-image-2.6.31.16-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.31.16-generic is not installed
root@ubuntu:/# 

```

So, any thoughts?

I should also mention that when I use the GRUB menu, I have tried three different kernels available to me, and all of them behave the same way. Would that possibly send us in a different direction for a fix?

---

### Post by rheide on 2009-12-15
Great news!

I happened across this thread ( [http://ubuntuforums.org/showthread.php?t=1355385]("http://ubuntuforums.org/showthread.php?t=1355385") ) and followed it's directions.

While I didn't see any menu to run clean-up commands, I was able to reboot and now life is good again.

Thanks.

---

### Post by martijn073 on 2010-02-11
Hello all,

For me restoring the symlink from /dev/disk/by-uuid/xxxxx to /dev/sdaX seems to do the trick. Don't know why the link was missing, but I only had two links left. One to Windows and one to the swap.

Cheers

---

