---
title: "Wiped HDD, no Win,. Still getting Grub Error 22"
date: 2010-01-31
forum: General Help
---

### Post by Ottis on 2010-01-31
A few weeks ago I posted that after upgrading to Ubuntu 9.10 on my Dell optiplex 210L, I continually got a "Grub Error 22" and "Grub Error 15" I could not boot to either Windows Xp or Ubuntu. I tried all suggestions with no luck.
Out of sheer frustration and having other things I needed to do (this is not my main PC) I decided to give it a rest and try again later.

So this time I wiped the HDD and installed 9.10 as the only OS, STILL getting Error 22!

Grub Loading Stage1.5.

Grub Loading, Please Wait...
Error 22

I disabled my slave drive with no change.

I had reburned the disk, did an error check, no change. I then re-downloaded from a different server, reinstalled, and still getting Error 22

My main PC is still running 8.04 and Im afraid to try to upgrade it now, (Both pcs are the same, Dell Optiplex 210Ls)

Any ideas????

---

### Post by meierfra. on 2010-01-31
> So this time I wiped the HDD and installed 9.10 as the only OS, STILL getting Error 22!

This is very weird. 9.10 uses Grub2, and "error 22" is  message from "Legacy Grub". So you still must have traces of your old install on your computer. Lets have a better look at your system. Please follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the  "RESULTS.txt"

---

### Post by Leppie on 2010-01-31
grub error 22 is a grub legacy error. karmic ships with grub2, so grub hasn't been installed properly during the installation process.
try the following:
- boot off a karmic livecd
- reset the mbr:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
- re-install grub2 onto your system:
```
sudo -i
mkdir /mnt/temp
mount /dev/sda1 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub grub-pc grub-common
apt-get install grub-pc grub-common
```
- if dpkg hasn't launched the configuration scripts for grub-pc and grub-common, run these commands as well:
```
grub-install --recheck /dev/sda
update-grub
```
reboot, grub2 should now load properly

---

### Post by Ottis on 2010-01-31
> **meierfra. said:**
> This is very weird. 9.10 uses Grub2, and "error 22" is message from "Legacy Grub". So you still must have traces of your old install on your computer. Lets have a better look at your system. Please follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the  "RESULTS.txt"

Well I booted to the live cd, downloaded, and after that Im afraid the whole thing went right over my head....

> **Leppie said:**
> grub error 22 is a grub legacy error. karmic ships with grub2, so grub hasn't been installed properly during the installation process.
try the following:
- boot off a karmic livecd
- reset the mbr:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```- re-install grub2 onto your system:
```
sudo -i
mkdir /mnt/temp
mount /dev/sda1 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub grub-pc grub-common
apt-get install grub-pc grub-common
```- if dpkg hasn't launched the configuration scripts for grub-pc and grub-common, run these commands as well:
```
grub-install --recheck /dev/sda
update-grub
```reboot, grub2 should now load properly

I tried this with no effect, rebooted, still grub error 22. Im thinking I didn't do it right, this is still new to me, Iv been using Ubuntu for about two years now without any trouble at all. 
I'll try again.

---

### Post by Ottis on 2010-01-31
WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device aufs as the root          &#9474; 
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block       &#9474; 
 &#9474; device. Either your fstab is broken and you should fix it, or you are     &#9474; 
 &#9474; using hardware (such as a RAID array) which this simple configuration     &#9474; 
 &#9474; program does not handle.                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/.    

?????

I have a single 80gb SATA Hdd and an ATA Hdd which I have disabled in my BIOS

EDIT; Im going to boot to my gparted cd and make sure the HDD was *completely* wiped before installing

---

### Post by Leppie on 2010-01-31
> **Ottis said:**
> WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device aufs as the root          &#9474; 
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block       &#9474; 
 &#9474; device. Either your fstab is broken and you should fix it, or you are     &#9474; 
 &#9474; using hardware (such as a RAID array) which this simple configuration     &#9474; 
 &#9474; program does not handle.                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/.    

?????

I have a single 80gb SATA Hdd and an ATA Hdd which I have disabled in my BIOS

EDIT; Im going to boot to my gparted cd and make sure the HDD was *completely* wiped before installing
that warning is only because you're booting off a livecd...
you can ignore it

---

### Post by Ottis on 2010-01-31
Well, i booted to my gparted CD and it seems that even tho I had disabled the slave drive in my BIOS (it was on the IDE with my optical drive) gparted could still see it and for some reason had not wiped the SATA drive but left a bunch of stuff on it.. (?) and installed 9.10 onto my slave drive (I think) why yes, I am a n00b...
So I have removed the slave (ATA) Hdd and manually wiped the SATA drive and am now reinstalling 9.10

Im sure this was just some n00b mistake on my part, but Im not sure what went wrong...

I'll post back and let you know if it worked right this time...

---

### Post by Ottis on 2010-01-31
That worked! Im not sure what difference it made but after removing the slave Hdd (even tho it was disabled in the BIOS) and manually wiping the SATA Hdd using gParted, everything installed and is working fine! 

First thing I saw;
**GNU Grub Version 1.97~beta 4**

Aaahhhhh... It worked!

Here's how it *was* set up;

Windows XP Home and Ubuntu 9.04, 1 Gb ram 
(1) 80 Gb SATA Hdd (contained Windows XP Home and Ubuntu 9.04)
(1) 250 Gb ATA Hdd installed on my IDE line along with my CD drive

Now that I think about it the 250 Gb Hdd was installed after I upgraded to 9.04 and before trying to upgrade (on-line) to 9.10
Maybe something about that configuration that Grub didn't like, but more likely something I was doing wrong, Im more comfortable turning a wrench on something greasy then tinkering with computers.
 
Thanks for your help

Ottis

---

