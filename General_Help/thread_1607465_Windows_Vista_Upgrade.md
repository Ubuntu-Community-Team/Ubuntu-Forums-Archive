---
title: "Windows Vista Upgrade"
date: 2010-10-27
forum: General Help
---

### Post by crackpotfox on 2010-10-27
Hello,
I run Windows Vista on my laptop computer along with Ubuntu 10.10 Maverick. I have finally decided to upgrade to Windows 7. Am I going to have to mess with GRUB to beable to get back into Ubuntu, like if you install Windows AFTER Ubuntu.
 
 
Again, I already have installed both Ubuntu and Windows, but will an ugrade break grub?
 
Thanks for any responce
 
Crackpotfox

---

### Post by sikander3786 on 2010-10-27
Yes upgrade to Windows 7 will break Grub. However it can be easily reinstalled. See here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by crackpotfox on 2010-10-27
ok, but are you SURE that this will work, i have had to reinstall ubuntu before, i did not like losing all of my custom themes and such...

---

### Post by sikander3786 on 2010-10-27
> **crackpotfox said:**
> ok, but are you SURE that this will work, i have had to reinstall ubuntu before, i did not like losing all of my custom themes and such...
It always works for me.

I am not frightening you but all the open source software and even the OS Ubuntu comes without any guarantees. So how can I guarantee that :-)

I just can say it should work. And if you don't seriously mess something up, we are always there to help you. Just don't overwrite Ubuntu partition with Windows and you'll be able to boot back into Ubuntu just fine.

---

### Post by crackpotfox on 2010-10-27
well, ok then thanks alot for the help ;)

---

### Post by crackpotfox on 2010-10-28
allright, I went to windows 7, followed this guide

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and all that i got after a reboot is a blank screen after the little underscore thing blinking at the top left of my screen... I'm suffering the slower-than-windows live cd booting and running, so a quick responce would be VERY appreciated,

thanks

---

### Post by Quackers on 2010-10-28
Sikander linked you to it before

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

The first command will give you your disk and partition number (for Ubuntu). The second command will use that disk and partition number. The third command will re-install grub to the disk (no partition number in this one). All from the Ubuntu Live CD

---

### Post by Mark Phelps on 2010-10-28
I hope this is not really BAD news, and I'm disappointed that no-one asked you BEFORE giving you advice -- but are you sure, really sure, that you had Ubuntu installed in its own separate partitions?

I'm hoping you did and did not, which I fear, have Ubuntu installed INSIDE Windows using a Wubi-install.  Because if it WAS a Wubi-install, it might be GONE now.  Depends largely on how well the Win7 upgrade was able to keep it intact.

To at least find out (unless you know for sure), boot from an Ubuntu LiveCD, open a terminal, enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out your partitions.

IF they all say NTFS, you've got a Wubi installation.  And, since Wubi does NOT use GRUB, then installing GRUB now is NOT going to help you.

---

### Post by crackpotfox on 2010-10-29
no, man i didnt do wubi, but heres the output of the command:



ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18b39c9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046   159782489    79890222    5  Extended
/dev/sda2   *   159782490   234438170    37327840+   7  HPFS/NTFS
/dev/sda5            2048   153838439    76918196   83  Linux
/dev/sda6       153838503   159782489     2971993+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


So, why does nothing happen after the little blinking underscore thing?

---

