---
title: "Screwed Up Grub!"
date: 2010-03-20
forum: General Help
---

### Post by klausner on 2010-03-20
I was trying to install Karmic onto a USB drive as a full install instead of a boot CD image, and I seem to have seriously screwed up grub on my hard disk as a result.

I'm running 9.10 64 bit with grub 0.97, NOT grub2.

I tried to restore grub from the 9.04 CD using the [instructions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Grub%20comes%20up%20in%20shell%20mode%20with%20no%20boot%20menu") at [help.ubuntu.com]("http://help.ubuntu.com"), specifically 
[INDENT]> sudo grub-install --root-directory=/media/disk-1 /dev/sda[/INDENT]
and that seemed to run without problems, but the system boots to the grub prompt.

Also tried [supergrub]("http://www.supergrubdisk.org/"). Supergrub has no problem finding the installed Linux kernels and the copy of Windows I have, and it has no trouble booting to karmic. But it doesn't seem to ***fix*** anything persistent. If I try booting the hard drive, I'm back to prompt. Booting from supergrub works fine.

Even tried reinstalling grub then running the grub-install incantation again.

My partition setup looks like this:
> [INDENT]Filesystem      Mounted on
/dev/sda5       /
/dev/sda2       /Windoze
/dev/sda6       /boot
/dev/sda7       /home
/dev/sda8       /usr/local[/INDENT]

I'm sure this is probably simple if I knew the correct grub syntax. Can someone clue me in?

---

### Post by Cfhs_1 on 2010-03-20
I don't know if this will help you any, but the last time I had trouble I used the synaptic package manager to completely uninstall grub, then I rebooted my computer and went back into ubuntu (using grub on an external disk) and reinstalled it through synaptic. My trouble was grub 2 doesn't like my computer yet. I wish you the best of luck!:popcorn:

---

### Post by klausner on 2010-03-20
> **Cfhs_1 said:**
> I don't know if this will help you any, but the last time I had trouble I used the synaptic package manager to completely uninstall grub, then I rebooted my computer and went back into ubuntu (using grub on an external disk) and reinstalled it through synaptic. My trouble was grub 2 doesn't like my computer yet. I wish you the best of luck!:popcorn:

Thanks for the response. Tried re-installing grub from synaptic, and then doing the grub-install mantra from the 9.04 CD. No improvement.

---

### Post by klausner on 2010-03-29
Bump

---

### Post by oldfred on 2010-03-29
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by klausner on 2010-03-30
> **oldfred said:**
> Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

This seems to be a great diagnostic tool. Unfortunately, I can't see anything wrong in it, but I'm no grub expert.

The output was nearly 400 lines, so I thought that was a bit much to put in quotes. The output file is attached instead.

Thanks for the suggestion and for future help.

---

### Post by oldfred on 2010-03-30
Minor points - boot flag is on linux partition. Linux does not use it windows does and some BIOS have to have it. Use gparted or command line to move boot flag to sda2.

set boot flag on for sda2 (off for others)
sudo sfdisk -A2 /dev/sda

sda6 has this:
/grub/menu.lst /boot/grub/core.img

sda5 has this:
 /etc/fstab

Sda6 is showing both grub legacy menu.lst and grub2 core.img and no fstab.

sda5 has no grub files. The grub legacy in the MBR says to boot from sda6. You also have grub legacy in the partition boot sector but do not need that. It is not used but will not cause any issues just being there.

Did you say you could get into your system with supergrub? If so we need to totally uninstall both versions of grub and reinstall which ever one you want. If parts of both are there it gets confused.

If you cannot get in your system we will have to chroot into it. Since you have 9.10 I would go to grub2, if you want grub legacy the instructions are slightly different grub is grub legacy and grub-pc and grub-common are grub2:

purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by klausner on 2010-03-30
> **oldfred said:**
> 
sda5 has no grub files. The grub legacy in the MBR says to boot from sda6. You also have grub legacy in the partition boot sector but do not need that. It is not used but will not cause any issues just being there.

Did you say you could get into your system with supergrub? If so we need to totally uninstall both versions of grub and reinstall which ever one you want. If parts of both are there it gets confused.

If you cannot get in your system we will have to chroot into it. Since you have 9.10 I would go to grub2, if you want grub legacy the instructions are slightly different grub is grub legacy and grub-pc and grub-common are grub2:

purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

Good news/bad news.

I uninstalled grub, and reinstalled grub 0.97. I suppose  I was afraid to remove something so fundamental before.

The system now boots, though the message that flashed by seemed to indicate that it was doing so from sda5.

The bad news is, no grub menu. Flashing messages certainly reference grub, but no choices for older kernels or recovery console.

Question: Yo said that > 
sda6 has this:
/grub/menu.lst /boot/grub/core.img

sda5 has this:
/etc/fstab

which would seem to make sense, since sda6 has the boot images and sda5 is the root partition. Am I missing something?

Thanks again.

---

### Post by oldfred on 2010-03-30
I thought the install of grub would create a new menu.lst or did you just install grub to the MBR?
IF you can get into your system sudo update-grub should create it. 

If you copy the menu.lst it would require major editing as all the UUIDs and (hd0,4) or (hd0,6) have to be updated. It woudl be easier/better to have grub create it. 

If you cannot get into your system then you will have to chroot into it and run the update-grub.

---

### Post by Liso22 on 2010-03-30
> **klausner said:**
> I was trying to install Karmic onto a USB drive as a full install instead of a boot CD image, and I seem to have seriously screwed up grub on my hard disk as a result.

I'm running 9.10 64 bit with grub 0.97, NOT grub2.

I tried to restore grub from the 9.04 CD using the [instructions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Grub%20comes%20up%20in%20shell%20mode%20with%20no%20boot%20menu") at [help.ubuntu.com]("http://help.ubuntu.com"), specifically and that seemed to run without problems, but the system boots to the grub prompt.

Also tried [supergrub]("http://www.supergrubdisk.org/"). Supergrub has no problem finding the installed Linux kernels and the copy of Windows I have, and it has no trouble booting to karmic. But it doesn't seem to ***fix*** anything persistent. If I try booting the hard drive, I'm back to prompt. Booting from supergrub works fine.

Even tried reinstalling grub then running the grub-install incantation again.

My partition setup looks like this:


I'm sure this is probably simple if I knew the correct grub syntax. Can someone clue me in?
I also screwed grub once to the point I couldn't even turn on the PC, it's desperating, I know it's not too much of an answer but it did fix itself with the live CD, I just run the recovery tools countless times and eventually it fixed

---

### Post by klausner on 2010-03-30
> **oldfred said:**
> I thought the install of grub would create a new menu.lst or did you just install grub to the MBR?

It did create a new menu.lst, because my Windoze partition isn't on it. But I know where the [instructions are]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to fix that. 

I *think* the absence of the grub menu was caused by the line > hiddenmenu
near the top of the menu.lst file. Maybe the default for it has changed or something.

Anyway, need to do a couple more reboots to test some things, then I might be able to mark this Solved.

Thanks again.

---

### Post by klausner on 2010-04-02
> **oldfred said:**
> 

purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

OK. After several rounds of testing, the nuke and recreate method seems to have done the trick. =D>

Manually added the Windows and Laptop recovery partitions. Windows 7 is hosed, but I'm pretty sure that's a whole different issue, since grub correctly tries to start it.

One added note for others in trouble: Remember that sda numbers start at 1, and hd numbers start at 0. so sda2==hd(0,1), and so on.

Thanks for all the help!

---

