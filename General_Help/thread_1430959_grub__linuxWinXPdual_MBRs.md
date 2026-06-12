---
title: "grub  linux/WinXP/dual MBRs"
date: 2010-03-16
forum: General Help
---

### Post by harryliddic on 2010-03-16
It all started with an ignorant installation of openafs-client that took up all my drive space. Needing the drive space for a project in video editing I was commission to do, I tried a fresh install but in my igorance I overwrote my WINXP drive so I ccorrected the drive problem and installed 9.10 on the correct drive. I then re-installed window on drive sda. Now I can't get back into liinux because windows has it own MBR. 9.10 is now stranded no way to boot it. Is the way off these horns of dilemna. I would like to restore the grub and I have read posts telling how to do it but they only work in linux.

---

### Post by prodigy_ on 2010-03-16
Wall of text... ;-)

Anyway, if I understand correctly, you have 2 (or more) HDDs. One has Windows (and Windows bootloader) installed. Another has Linux installed but no working bootloader at all.

If so, there are two good options:
- (more comfortable) boot from Live CD and replace Windows bootloader with GRUB;
- (safer) disconnect Windows HDD, boot from Live CD and install GRUB on Linux HDD.

The 2-nd option is preferrable if you want both installations to be completely independent from each other. But you'll need to call BIOS boot menu (usually F8 key) during POST every time you'll want to boot into the secondary OS.

---

### Post by lordskid on 2010-03-16
> **prodigy_ said:**
> Wall of text... ;-)
The 2-nd option is preferrable if you want both installations to be completely independent from each other. But you'll need to call BIOS boot menu (usually F8 key) during POST every time you'll want to boot into the secondary OS.

just to add:

you can dd the boot loader off your linux partition and save it to your windows filesystem as a file e.g. ubuntu-loader

then edit your windows boot.ini

add this line to the end of the file

c:\ubuntu-loader "Ubuntu Karmic"

see [http://karmic-koala.totalh.com/index.php?p=1_6_Short-Tutorials]("http://karmic-koala.totalh.com/index.php?p=1_6_Short-Tutorials")

whenever you boot you will be given a choice of ubuntu or windows...

---

### Post by l4zy on 2010-03-16
I would install grub with live-cd. It's really easy + it's a bit easier to choose where to boot linux / win .. or any other OS. 

It takes about 2-3 mins to install grub with live-cd.

---

### Post by soltanis on 2010-03-16
Like above said, install grub with a live CD. Don't bother with the Windows MBR bootloader; grub does fine and is easier to configure.

Try this tutorial:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by lordskid on 2010-03-16
> **soltanis said:**
> Like above said, install grub with a live CD. Don't bother with the Windows MBR bootloader; grub does fine and is easier to configure.

Try this tutorial:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Well I agree with the last 2 posts. I took some 4 months before doing away with windows boot loader and I never looked back since.

---

### Post by Mark Phelps on 2010-03-16
If I understand your situation, you have two physical drives, one with XP installed (and "Windows MBR") and the other with Ubuntu installed.

An easy solution would be to do the following:
1) Install GRUB2 to the Ubuntu drive (if not already there)
2) Boot from the Ubuntu drive
3) Once in Ubuntu, open a terminal and enter "sudo update-grub"

Should generate a new GRUB2 menu, so the next time you boot, you will have access to both OSs.

---

### Post by harryliddic on 2010-03-16
thanks for all the excellent advice. The LIVE CD is the way I went and all worked out well. Thanks again

---

