---
title: "Love Ubuntu, but can't boot again"
date: 2011-02-03
forum: General Help
---

### Post by tweakerr on 2011-02-03
I love Ubuntu. I like how fast it installs. I love how it has become MUCH more user friendly than the previous distro of Linux I used (Redhat somewhere in late nineties). And I love how it's fast, efficient and how it does pretty much everything I want out of my laptop.
But now, just before I wanted to move al my old windows files to my ubuntu home directory permanently, everything has frozen up. 
I get the following error after trying to boot, and I don't have a clue what to do about it. Could anyone point me in the right direction?

```
[     3.093786 ] ---[  end trace 79b7836bb110e70f   ]---
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

Busybox v.1.15 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```I have done the following things since the last succesful boot and before I got this message: 
Encrypted my home folder using ecryptfs
Ran Virtualbox for the first time and deleted a few 'filesystems' that didn't work
Installed the new kernel (x.35 I believe?).

If the problem is the ecryptfs, the new kernel or the virtualbox, I'd part with it without hesitation and be happy to enjoy Ubuntu again.
But what's the problem and how do I fix it?


EDIT: maybe I should add that I installed while windows 7 is still in my MBR. Is that relevant?
EDIT2: removed some excess info

---

### Post by mastablasta on 2011-02-03
> **tweakerr said:**
>  
EDIT: maybe I should add that I installed while windows 7 is still in my MBR. Is that relevant?

 
yes very much relevant as you installed the OS within windows, run it in virtualization of sort and now you are trying to remove windows. how strange is that?
 
anyway i believe there is a solution that will help you get to your data. but basically you should have updated unless a couple of packages are locked.
 
check here for solution: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
If you didn't install it via wubi then please post the output of bootinfoscript.
insctructions and script available here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
good luck with solving you problem. next time install it side by side. ;)

---

