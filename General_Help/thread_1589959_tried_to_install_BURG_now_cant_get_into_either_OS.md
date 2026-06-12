---
title: "tried to install BURG now cant get into either OS"
date: 2010-10-07
forum: General Help
---

### Post by Circlethesky on 2010-10-07
hi all
im totally new to ubuntu and recently installed it alongside windows 7
just now i tried to install BURG by copying a code i got from a website (dont remember which) into a terminal 
when i restarted my computer to see if it had worked the following came up
 
 
 
BURG version 1.98+20100623-1 
 
Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists possible 
device or file completions.
 
grub> 
 
 
 
iv looked at every solution from every related forum post but i still cant get into either operating system on my computer.
i dont have either of the installation discs which is why i really need to be able to get back into windows, as well as my files and settings. i dont mind if i have to completely remove ubuntu and everything to do with it, as i can easily set that up again in a matter of minutes. right now i just need a way to return my computer to how it was before i installed ubuntu 
please help!

---

### Post by sikander3786 on 2010-10-07
You have got a Windows disc? If so boot into it and then fixmbr. After that you will be able to boot into Windows.

[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

You have installed Ubuntu via Wubi, I am not sure if BURG works with it or not. And Grub might also not work. So the better option is to restore MBR from Windows Disc and reinstall Ubuntu. Better if you have got some space and install it side-by-side Windows.

---

### Post by Circlethesky on 2010-10-08
thanks for the reply
i dont actually have the windows disc, i got the computer with windows 7 proffessional already installed, the only disc i got with it was for the graphics card
yeah, if i can get it back up, i definately wont be trying to install burg again

---

### Post by Quackers on 2010-10-08
If you Google about you can download a Windows repair disc then you can fix booting Windows.

---

### Post by wilee-nilee on 2010-10-08
Is this a wubi install?

Here is a recovery disc link.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

If this is a wubi just use the recovery disc and run the highlighted command from the command line, on the booted disc per the instructions.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by tacticalbread on 2010-10-08
Well, I managed to get myself in the same boat as you, because I thought I knew how to fix it ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) but that didn't work with the 10.10 RC disc. I'm pretty sure it did with the 10.04 disc, so if you're not on a Wubi install, you should try that.

edit: Remembered that 10.10 uses GRUB2, so that's why that didn't work lol. Ended up following [this](http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05) and that fixed it.

But since you're on Wubi, I'm being of little help to you.

---

### Post by Circlethesky on 2010-10-12
thanks guys, managed to get my hands on a windows disc so i ran the repair so it just boots to windows now
is there a quick way to get back into the ubuntu that i already have installed? or will i have to use the disc to reinstall it?
 one thing is for sure and that is i will not be attempting to install BURG again!

---

### Post by tacticalbread on 2010-10-14
You can rename your Ubuntu 'disc' (I forgot what it's called but I think you can find it in C:\wubi\disks) to something else, install Wubi, then replace the install 'disc' with your previous one, and you should be all good.

---

### Post by nzjethro on 2011-06-12
After installation, don't forget to run
```
sudo update-burg
```
And I recommend running
```
burg-emu
```
This allows you to check that it was properly installed.
If you have already restarted (chances are you have looking seeing as the message has come up) boot from a live CD, mount your Ubuntu partition, chroot in, and run update-burg from there. Burg is awesome, don't let one mistake put you off!

---

