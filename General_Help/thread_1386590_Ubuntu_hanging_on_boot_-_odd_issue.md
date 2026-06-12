---
title: "Ubuntu hanging on boot - odd issue"
date: 2010-01-20
forum: General Help
---

### Post by Tronman on 2010-01-20
Hi everyone! I'm having a bit of a problem booting into my Ubuntu installation, but first, a bit of history:

My machine had five main partitions:

1. A Windows XP Recovery Partition (~2 GB)
2. A Windows XP partition (~30 GB)
3. An extended partition with (~62 GB)
    3a. A Windows XP data partition (~30 GB)
    3b. An Ubuntu partition (~ 30 GB)
    3c. A Linux swap partition (~2 GB)

My eventual goal is to turn the XP partition into a virtual machine, and have Ubuntu as the only OS on the hard drive. But I'm not quite there yet.

First, I backed up all the data on the Windows XP data partition onto an external drive. Then I booted into the GParted LiveCD, removed the Windows XP data partition, and added the space to the Ubuntu partition (this required moving the partition to where the data partition was).

Upon rebooting, GRUB was no longer functioning. I would receive the following:  
GRUB Loaded.
error: unknown filesystem
grub rescue > 

Upon doing some research, I decided to reinstall Grub using the instructions found here: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

That brought my Grub back happily, and I could boot to the XP partition no problem. But when I try to boot into the Ubuntu partition, I simply get a blinking cursor for about 10-15 seconds, followed by the Ubuntu logo for another 10-15 seconds, followed by another blinking cursor until I power off the machine.

I can boot into the Ubuntu recovery mode with no problem though, then login on the command line and run startx and everything is running the way it should. So things are almost running the way they should be, expect for this odd error with the standard boot option. Everything looks to be pointing to /dev/sda5 which should be the right partition.

I probably won't be able to respond for a day or so, but if anyway has any advice I'd be happy to have a look at it!

Thanks.

---

### Post by Tronman on 2010-01-20
Two quick things I forgot to mention:

1. Running Ubuntu 9.10 on a 64 bit syste
2. When I use the recovery option to boot to a command prompt, I get an error saying:
Could not stat the resume device file '/dev/sda7'
Please type the full path and try again

At which point I'll put in /dev/sda6, then I get to where I can log in. /dev/sda7 no longer exists (was the swap partition), but now that is at /dev/sda6. I don't know what's still trying to refer to /dev/sda7. I thought maybe fstab but that appears to be using the correct partitions.

Also, I noticed that 

1. I can no longer mount my XP partition from inside Ubuntu though I could before (with root password). Now I get a "Unable to mount location Not Authorized" error and it doesn't even prompt me for a password.

2. Under "Places" I used to always see the Ubuntu partition, I now only see the XP and XPRecovery partition (going to the file system, however, seems to be the Ubuntu partition).

Thanks!

---

### Post by john newbuntu on 2010-01-20
Once you logon to Ubuntu properly (via the recovery console), type
```
sudo update-grub2
```Hopefully that should make things better.  If it does not fix your problem, then edit  the file: /etc/default/grub and change:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
Again run sudo update-grub2 and see if fixes the issue.

Now, when you used gparted and extended your logical partition, did you do a swapoff on your swap partition and redo the swapon on the new partition? Anyways, just to set swap properly,
```
sudo swapoff -a
sudo /sbin/mkswap /dev/sda6
sudo swapon -a

```That should fix your swap partitions.  Also make sure  that the swap is correctly pointed to in /etc/fstab.

---

### Post by _H3MLOCK on 2010-01-20
First of all, label the sda numbers on your list of partitions(you can find out which is which using Gparted)... And post the contents of /boot/grub/menu.lst

By what I can see, sda5 should be your boot partition for ubuntu not sda7 (which is why I asked for labels) This could be an issue with kernel discovery, have you tried using a symlink?

---

### Post by Tronman on 2010-01-21
Hey guys, thanks for your responses!

> **john newbuntu said:**
> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
Again run sudo update-grub2 and see if fixes the issue.


Ahh...that allowed me to enter the partition upon boot like I had been seeing see in the recovery console. Entering it and it booted properly.

> **john newbuntu said:**
> 
Anyways, just to set swap properly,
```
sudo swapoff -a
sudo /sbin/mkswap /dev/sda6
sudo swapon -a

```That should fix your swap partitions.  Also make sure  that the swap is correctly pointed to in /etc/fstab.

Done, and I made sure the UUID outputted by /sbin/mkswap was pointed to in fstab. 

Unfortunately, I still get asked:

resume: Could not stat the resume device file '/dev/sda7'
Please type in the full path name to try again or press ENTER to boot the system:

message. To be fair, I don't even have to type anything here, just hit enter and the system starts as normal.

After some digging, it seems the "resume" it's referring to is actually the suspend function which can't find the swap partition.

I then edited /etc/uswsusp.conf which showed /etc/sda7 and ran
dpkg-reconfigure uswsusp, and reset the configuration settings, and now I can boot normally again (but it seems to be slower oddly, and even though I put splash back into "GRUB_CMDLINE_LINUX_DEFAULT", I still see some output on boot about /dev/sda5 and libcrypt.

My suspend causes the computer to immediately wake up though as soon as it enters suspend (but I'm pretty sure that was the case even before this). Hibernate seems to work okay. 


> **_H3MLOCK said:**
> First of all, label the sda numbers on your list of partitions(you can find out which is which using Gparted)... And post the contents of /boot/grub/menu.lst

By what I can see, sda5 should be your boot partition for ubuntu not sda7 (which is why I asked for labels) This could be an issue with kernel discovery, have you tried using a symlink?

Thanks, but I don't have a /boot/grub/menu.lst. I remember reading somewhere that grub2 doesn't use it. In any case, it seems to have been an issue with the swap/suspend function, not the booting partition

Thanks again!

---

