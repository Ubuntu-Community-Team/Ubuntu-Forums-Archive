---
title: "Ubuntu 9.10 Mounting error - No such file or directory. No init found."
date: 2010-04-07
forum: General Help
---

### Post by specialk1st on 2010-04-07
*_Ubuntu 9.10 Mounting error - No such file or directory. No init found._*

Hello,

I am using a Ubuntu 9.10 with GNU GRUB 1.97~beta4 on an IBM Thinkpad.

I shut down my computer like normal and when I tried to start it up again it does this:
First, it goes to the boot menu, and when I selected the normal mode it doesn't get to the login screen.  Then, when I go to the recovery mode I get this error:

[B]Begin: Running /scripts/init-bottom ...
Begin: Starting AppArmor profiles ...
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)[/B]
**Enter 'help' for a list of built-in commands.**


So I went to Google and found this post, ([http://ubuntuforums.org/showthread.php?t=1437015](http://ubuntuforums.org/showthread.php?t=1437015)) which says that the grub needs to be reinstalled. So I entered the 1st command with my LiveCD running, but when I enter the 2nd command: 

"**sudo mount /dev/sda1 /mnt**" (without the quotes)

I get this:

"[B]wrong fs type, bad option, bad superblock on /dev/sda1, 
missing codepage or helper program, or other error 
In some cases useful info is found in syslog - try 
dmesg | tail or so[/B]" (without the quotes)


Please help me.  I cannot just do a fresh install of Ubuntu because I will lose some very important data. :confused:

OK, so here is the update:

I went to this website ([http://www.linuxquestions.org/questions/linux-hardware-18/mount-wrong-fs-type-bad-option-bad-superblock-dev-hdc3-373428/](http://www.linuxquestions.org/questions/linux-hardware-18/mount-wrong-fs-type-bad-option-bad-superblock-dev-hdc3-373428/)) and used the solution post #6 by "Crappy" at "11-07-2005, 6:28PM".

After entering: **sudo fsck /dev/sda1**

I then chose the "yes" option until I got a message saying that it finished.

Then I entered: **sudo grub-install --root-directory=/mnt/ /dev/sda**

(I made a mistake when entering this that others should be aware of... it is "sda" only, not "sda1".)

I then restarted the system without the LiveCD.  Selected the normal (non-recovery mode) default linux from the bootmenu.

This time my login screen showed up!  So I logged in like normal.

Finally, I went to the terminal window and typed: **sudo update-grub**

After this finished I closed my terminal window and restarted my computer one last time to make sure all the changes were updated properly.

Problem fixed!

---

