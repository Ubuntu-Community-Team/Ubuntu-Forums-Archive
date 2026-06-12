---
title: "&quot;Gave up waiting for root device.&quot; -- 10.04 x64"
date: 2010-07-30
forum: General Help
---

### Post by kreuelt on 2010-07-30
Today, I tried to install Lucid x64.
I have a Dell Studio 1555 with a 250gb hard drive. I have it partitioned thusly:
A 200GB NTFS partition that I keep all my music/videos/books on. When I have Linux installed, I mount this as /files. I never touch this partition during an OS install.
A 100MB EXT4 partition that I created today during the install process. I mount this as /boot.
A 4GB swap partition that I created today during the install process.
A 46GB(ish) EXT4 partition that I created today during the install process. I mount this as /.
As far as I could tell, aside from being for some reason painstakingly slow, the install process went normally. At the end, I was prompted to remove the disc and press Enter to reboot. I did so.
My computer didn't boot. Instead, after BIOS, I got a blinking text cursor for about ten seconds, and then the following message:
> Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{my hard drive's uuid} does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter "help" for a list of built-in commands.

I've tried setting rootdelay=90, but that didn't work, and the majority of the failure output is greek to me. I've found reports of similar problems all over the forums, but nothing really useful or comprehensible. Do any of you have any advice to offer? Thank you!

---

### Post by Elfy on 2010-07-30
I would start by checking the UUIDs from the system and in fstab - you'll need to do this in the livecd.

```
sudo blkid
cat /etc/fstab
```

You would need to mount the installed system - as you might also need to update-grub from within the livecd - follow this [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) from the  METHOD 3 - CHROOT to get the install mounted and then check the above before updating grub.

If you do need to edit fstab 

```
sudo nano /etc/fstab
```

Then run the update-grub commands.

---

### Post by P4man on 2010-07-30
It could also be worth going in to your bios and checking the SATA settings and see if changing them to ACHI (or "compatibility mode") helps.

---

### Post by Tazman34685 on 2010-11-15
So I powered off my system without properly shutting down the system and Now I'm getting the same error:
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{my hard drive's uuid} does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter "help" for a list of built-in commands.

I've tried the attached methods without success, and now I about to just re image the  system.
(the attached screen shots show the current system\drive set up) I anyone feels like they can Help PM me.. I have learned the valuable lesson that YOU Should Never Just Power Off An Ubuntu System......

[IMG]http://img.photobucket.com/albums/v517/tazman34685/sudoblkid.png[/IMG]

results from sudofdisk
[IMG]http://img.photobucket.com/albums/v517/tazman34685/sudofdisk-l1.png[/IMG]
[IMG]http://img.photobucket.com/albums/v517/tazman34685/sudofdisk-l2.png[/IMG]

---

### Post by Neno505 on 2010-11-15
Hello! 

I have a problem with Intel MKL lib! I never worked with MKL and am trying to run a fortran program .for in command prompt using Intel MKL, how do I do that! I have installed my MKL 10.3 in c:/Program files and g77 fortran compiler in c:/f. What do I do next? 
(g77 works fine) 

Thank you very much for your help!

---

