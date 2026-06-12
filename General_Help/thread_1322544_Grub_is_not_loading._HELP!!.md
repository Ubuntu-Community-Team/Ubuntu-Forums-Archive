---
title: "Grub is not loading. HELP!!"
date: 2009-11-11
forum: General Help
---

### Post by white-zilla on 2009-11-11
Hello, I dual boot windows 7 and ubuntu 9.10.  I was running windows 7 and I wanted to boot into ubuntu. So i restart my system to bring up grub. Only problem is, is that grub never loads. 

Once my motherboard splash screen pops up, I just get a black screen saying "Grub is loading." and it just keeps saying its loading while nothing happens, so i have no options to boot into anything.  My system at the moment is completely useless.  any help is appreciated.

---

### Post by jnorthr on 2009-11-11
You HAVE backed up your important data, haven't you ?

It would help if you've burned a live CD of ubuntu, then you could at least boot from there and we could fix your system more easily. You could also try to power off your system, wait a minute then reboot. Sometimes this fixes the issues. Is there any BIOS choices offered to you to do a safe reboot ? You could try one of those, if available.

---

### Post by white-zilla on 2009-11-11
first things first, yes, i'm using a live disk of ubunu currently.  And i'm using it to back up what little valuable data I have ATM, so if I gotta nuke my hard drive, I can do it.

I've tried shutting down and restarting my system several times...no luck.  I'll check my bios for a safe boot.

---

### Post by jnorthr on 2009-11-11
which o/s did you install first ? sometimes that will dictate which boot load manager is being used. Doubt the windose version will play nicely with ubuntu. Is there a boot option from the live CD ? guess you tried that too. Does windows boot ok ?

sounds like the grub 2 version of boot loader is not happy on your kit. Just trying to think how we could refresh your boot loader with the prior version of grub used under 9.04, which worked ok for me.

---

### Post by white-zilla on 2009-11-11
I installed windows 7 first.

Since Grub is a linux application, would I be able to boot into windows if i deleted my installation of ubuntu on my hard drive?  I'm thinking that nuking ubuntu might be the quickest and easiest fix in case we cant come up with a fix

---

### Post by wilee-nilee on 2009-11-11
> **white-zilla said:**
> I installed windows 7 first.

Since Grub is a linux application, would I be able to boot into windows if i deleted my installation of ubuntu on my hard drive?  I'm thinking that nuking ubuntu might be the quickest and easiest fix in case we cant come up with a fix

If you remove the Ununtu you have to do a fixmbr to get the W7 bootloader back. I have W7 and Karmic on my net book with no problems, so you have a couple of options.

---

### Post by white-zilla on 2009-11-11
Do you think i'd have any luck if I just did a fixmbr and left ubuntu on?  I problably wont be able to get into ubuntu, but all my valuable data is on win7.

How about re-installing grub? is there some way I can update/re-install it from a live-disk?

---

### Post by white-zilla on 2009-11-11
Do you guys think i'll have any luck if i follow this guide and re-install my grub?

[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

---

### Post by Databit on 2009-11-11
Give this a go:
List all partitions:
fdisk -l

Note these down. If you only have 1 Linux, 1 Swap and 1 Windows then the 1 linux will contain your /boot mount point

create a directory to mout too
mkdir /media/sda1mount

Mount the boot device (replace the sda1 with the device that your /boot is on)
mount /dev/sda1 /media/sda1mount

Now check to see if this mount has the /boot
ls /media/sda1mount

you should see a directory for the boot. If not try mounting the other linux partitions
Once you have found it reinstall grub (change mount point and device as necessary):
sudo grub-install --root-directory=/media/sda1mount /dev/sda

You should see an success message of some type. 

Now pull out the cd and reboot. This should boot to linux

edit the grub boot menu:
sudo gedit /boot/grub/menu.lst

Down in the bottom of the list check to see if Windows is in the options. It will say 'title Windows...' if it is. If not then add (replace hd0,0 with your windows partition info. 

title Windows Inferior OS
rootnoverify (hd0,0) 
makeactive
chainloader +1

---

### Post by Databit on 2009-11-11
if you have a problem with this then give us a copy of 
fdisk -l

---

### Post by white-zilla on 2009-11-11
kk, i'll do that first thing once i get back from work and i'll let you know how that goes.

...Couldn't i just mount the linux partition by clicking on it and then just change 'sudo grub-install --root-directory=/media/sda1mount /dev/sda' accordingly?  (i'm thinking sda1mount will be the only part of the command that needs changing.)

---

### Post by white-zilla on 2009-11-11
Its working. good call databit

---

### Post by white-zilla on 2009-11-14
okay, it only sorta worked.  Everytime I run windows it kills grub so i gotta keep re-installing it.
any ideas for a permanent fix?

---

