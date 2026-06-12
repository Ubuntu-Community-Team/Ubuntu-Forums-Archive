---
title: "karmic koala problems"
date: 2010-01-04
forum: General Help
---

### Post by Drakkenkill on 2010-01-04
Hi i've had alot of problems with karmic koala but i think i should blame it on my computer damn things ancient anyways i want to install puppy linux because karmic requires all of my ram to operate but the only problem is that i can't get my CD-RW drive to burn i've ran an image burn through k3b brasero and gnomebaker and everytime i try to burn the image my computer freezes up i'm ready to pull my hair out i want to get puppy linux on this thing so it'll run faster is it because i'm trying to do too much with not enough RAM if so is there a few extra programs i can suspend untill i have burned the OS or am i missing some kind of file or program or what i mean i can't even get the disc back out even if it unfreezes i still have to restart the system just to get the disc out i know it can't be my disc drive it's not new but it's never been used till now and it didn't come with a driver disc so it can't be that either all i want to do is get puppy linux installed and move on with my life until i buy a new computer then i'll just install the lastest ubuntu version at the time if anyone can provide some solid assistance please help i deal with electronic hardware repair this software stuff is killing me!!!!!

---

### Post by alwayshere on 2010-01-04
if you hav an iso image to burn just right click on it a choose write to disk .
that might use a little less grunt?

---

### Post by amsterdamharu on 2010-01-04
No need to put puppy on a cd, you can put it on the harddisk or usb. 

Open the iso with archive manager or archive mounter, copy the files to usb In the root of usb make copy isolinux.conf to  syslinux.conf.

If your usb is /dev/sdb and the files are on the first partition you can make it boot by issuing the following command:
syslinux /dev/sdb1

Now boot the computer from usb or if you copied to harddisk boot from harddisk.

If you have grub on your harddisk then just copy the files of the iso to root folder and add this in grub.conf or menu.lst

title        Pyppy
root        (hd0,4)
kernel       vmlinuz
initrd        initrd.gz pmedia=cd

The root you have to figure out which one it is, when you boot and have the menu you can press c for commandline and then type
find /vmlinuz
This will give you the hd where the vmlinuz is.

---

### Post by SuburbanMe on 2010-01-04
I know this isn't what you are asking about - but before i installed Ubuntu KK on my Laptop, i ran a version of Linux Mint on here, I also installed it onto my mums laptop as she was also switching over to linux from Windows.

The one thing i found with Mint was that it pretty much had everything that someone would need pre installed. drivers weren't a problem, there was no issues what-so-ever.

I've had a few issues with KK - but nothing that will make me question my decision (yet).

Anyway, just thought I'd give you a heads up on mint - it's basically ubuntu with everything preloaded. Only downside - not alot of support for it yet (forum wise), but anything you need can be directly translated from ubuntu to Mint without any issues.

Enjoy!

---

### Post by JBA2337 on 2010-01-05
The new Karmic Koala, Ubuntu version 9.10 definitely has a bunch of problems that I never experienced with version 9.04. I have used the last 3 different versions of Ubuntu, 8.04, 8.10, and 9.04, with hardly any problems, but after installing Karmic Koala, version 9.10, I have had nothing but problems. So I switched back to version, 9.04. By the way, I did a clean install of 9.10. I formatted my Linux Ext3 partition before installing version 9.10.

I definitely am not going to use version 9.10 for now. Maybe some of these problems can be fixed when 9.10 is updated. Most of the problems mentioned below have not been posted in the Ubuntu Forum. Rather than spend a lot of time trying to post every problem and fix them one-by-one, it was easier for me just to go back to 9.04. I know that 9.04 works well on both my computers. (I have a home-built generic desktop computer and a Toshiba laptop.)

Here is a list of the most bothersome problems that I have had with version 9.10.

(1) I had to burn the 9.10 iso file to a CD disk 3 times to finally get one that had no errors. (With version 9.04, I only had to burn one disk, and it still works perfectly). I used the same software (Nero) and the same computer to burn all of the CD disks, so I don't see how the bad 9.10 disks could be a hardware problem.

(2) When I tried to install version 9.10, the process failed at least 4 times before I finally got a successful installation. The computer simply locked up, and quit loading the program. On the exact same computer, this NEVER has happened with version 9.04.

(3) With version 9.10 there is no sound at all; I can't play CD's or mp3 files.

(4) The following is not a problem, just a comment...In version 9.10 the new "Software Center" is, in my opinion, definitely not an improvement over the previous version. In version 9.04 the "Add/Remove Applications" program is much easier to use, and if I want to I can install or uninstall 15 or 20 software packages all at the same time. The new Software Center only allows me to install or uninstall ONE software package at a time. The new 9.10 Software Center is not an improvement, rather it is a step backwards. The only solution to this problem would be to only use Synaptic Package Manager to install or unistall software.

JBA2337

---

