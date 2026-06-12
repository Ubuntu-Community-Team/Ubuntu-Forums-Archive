---
title: "Moving Ubuntu to Ubuntu?"
date: 2006-02-05
forum: General Help
---

### Post by doomfiend on 2006-02-05
Okay, so I've been playing around with Ubuntu for a few weeks (my first foray into linux) and got along allright.  All the guides for gcc3.4 and ndiswrapper and wpa_supplicant got me through my intitial woes.  So then since I got that all set up and automatix running I wanted to Ghost my Ubuntu partition to my other drive.  I had XP Pro on my master IDE (100GB, hda) and Ubuntu on my slave IDE (40GB, hdb).  I decided to totally wipe clean my hda and just put a little 20GB partition for XP, and have a enough for a 40GB partition to ghost my Ubuntu partition to, and 40 to play with.

Anyways, I forgot to back up the boot record and XP's reformatting totally abolished my MBR.  So, resigned to starting up the whole process again, I reinstalled Ubuntu on a 40GB partition.  Lo and behold, when I got through it all and restarted, what was on the Grub Bootloader but my old partition!

So after all that crap, I want to basically copy over the stuff that's in my original ubuntu partition on my slave drive to the new Ubuntu on my primary drive, because the other drive is going into a little clunker I'm putting together as a server so I can have a little test lab set up at home for my networking classes.  Can I just copy over certain whole directories and files and have it work exactly like my setup is now, or is there a program I should use?  Any heko would be appreciated.

---

### Post by Ocxic on 2006-02-05
ok this is actually really easy to do, from you post I goin along with the fact that ubuntu is on hdb, and windows/freashly formatted partition is on hda

simply enough COPY (do not move incase something goes wrong) ALL of your current ubuntu data from hdb to hda (this means everything from hdb to hda).

then install grub to hda - I'm not sure how to do this, but there is an guide somewhere and it's easy.

then reboot you computer, while hdb is iether unplugged or disabled somehow this way you'll know if everything works, just plug in/re-enable your hdb, then just format hdb and you good to go with ubutu now on hda.

Don't forget to recreate your swap partiton. TIP: haveng your swap partiton on a different disk then your ubuntu installation will improve performance of the swap space. ie: you can just keep the swap space on hdb and edit your /etc/fstab to point to the right partition.

Do everything from the live cd, just so your not moving files from a running system

---

### Post by dcstar on 2006-02-06
If you change a Ubuntu installation from hdb to hda (or anything to anything else), I believe you will get a "pivot_root" error when booting.

Apparently this is because the install disk is hard-coded into the /boot/initrd file, and this has to be modified to allow booting from a different drive designation to what was used for the install.

This possibly could be done by a quick re-install preserving all the data on the drive, but some research has revealed that the "mkinitrd" process is required to recreate this file with the correct hard drive device:

Edit your /etc/mkinitrd/mkinitrd.conf file, and change:

ROOT=probe

to 

ROOT=/dev/hda (or hd whatever your new boot drive will be when you move the drive)

then:

sudo mkinitrd -o /boot/new-initrd.img

and then edit you /boot/grub/menu.lst file to use this new boot image (copy the existing stuff so you don't overwrite it) and also to use the new root drive designation.

This should work (in theory), but someone will have to try it and let us know the results.

---

### Post by majed on 2006-02-06
or u can just copy the directories /etc , /usr , /opt , /var , /home from the old installation to the new installation and then reboot!

ps: maybe u'll need more directories to be copied as well...

---

