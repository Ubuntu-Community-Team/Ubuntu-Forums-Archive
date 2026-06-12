---
title: "UEFI/Graphical Issues"
date: 2012-04-14
forum: General Help
---

### Post by Tuxqi on 2012-04-14
OK.. I've asked for help in the linuxquestions forums but so far had no responses so now I am going to try for help in here.

I have just built a new PC.. all the hardware seems to be working fine.
/
The motherboard is MSI x79a-gd45 (8d)  and has an nvidia graphics card in it.

It's the first UEFI system I have owned/used so there were a few things I was unaware of like needing the boot disks to be UEFI compatible.

So I downloaded Ubuntu as I knew it could boot with UEFI. The GRUB Menu appears but every time I try and boot an option the screen just goes black and I can't progress any further.

The disk seems to be loading everything (I can hear it) and the screen has no 'out of range' message.

I have tried editing a few boot options I have read about like:

'nomodeset' and a few of the other options that often get suggested... only one I haven't tried yet is: 'nv.modeset=0'

I have tried an old nvidia card I have but same thing happens.

I am stumped. please help.

---

### Post by niglas on 2012-04-14
See if you have any luck with this guide:
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

---

### Post by Tuxqi on 2012-04-14
> **niglas said:**
> See if you have any luck with this guide:
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

Thanks but my problem isn't the installing  (although some useful knowledge in there for later).

I can't get past grub on the cd.  Graphics wise I can get into the UEFI BIOS and see the grub screen (only displays in a basic mode tho) but what ever option I try to boot the screen just goes black.

I've tried adding nomodeset, etc, on the parameters by clicking e.

Every option I've tried leads to a  black screen but I can hear the disk booting up.

So I'm not even able to get to a text based mode to do anything.

---

### Post by oldfred on 2012-04-14
With the CD or USB you are not booting with grub. Have you actually gotten a grub menu where you add nomodeset?

Normally with liveCD you have to immediately press a key (accessibility circle and keyboard icons at bottom of screen), and then press f6 and choose nomodeset as a boot option.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some have had to add other parameters also:
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

---

### Post by Tuxqi on 2012-04-14
The Disk boots and then I get the grub menu (although it's a much more basic version.. like a failsafe version and it's just black/white).

I edit the options manually by pressing e.

I've had a look at those threads you linked... tried the one with the boot options 'rootdelay'  but that didn't work either.

---

### Post by oldfred on 2012-04-14
If you are getting the grub menu, remove quiet & splash and it should show the boot process. Many text lines will go by, we are trying to see repeated attempts at loading a drive or driver, or an outright failure to load something. The same info is in the log files.

The other choice in a grub menu should be recovery mode, can you boot that?

Or are you getting a boot menu from UEFI? That is before the grub menu.

---

### Post by Tuxqi on 2012-04-14
I am definitely at the grub menu.

I removed the quiet and splash options.. press f10 and...

still a black screen.

---

### Post by oldfred on 2012-04-14
After editing grub menu, use control-x to boot.

---

### Post by Tuxqi on 2012-04-14
when I try that it just types the letter 'x' instead of booting.. only way it booted was by pressing f10.

---

### Post by oldfred on 2012-04-14
I thought maybe they had fixed some of the bugs.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
[COLOR=Red]ctrl-x does not work in grub-efi[/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

### Post by Tuxqi on 2012-04-14
is there a difference between using f10 and ctrl+x?

---

### Post by oldfred on 2012-04-14
Not sure if then you have used the changed settings or not? Results seem to say not as if you have removed quiet splash then you should at least see some commands scroll by.

Were you able to boot from liveCD? or did that also have same issue?

---

### Post by Tuxqi on 2012-04-14
thats what im using a live cd to try and install the system  and no I cant get into any text or graphical environment.. the moment I start booting anything.. it juts goes black.

---

### Post by oldfred on 2012-04-14
From liveCD, you should get the first two screens like shown here. You have to press a key to get the second. Maybe with UEFI it works differently?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

