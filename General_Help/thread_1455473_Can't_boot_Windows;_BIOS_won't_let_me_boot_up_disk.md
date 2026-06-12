---
title: "Can't boot Windows; BIOS won't let me boot up disk to fix it"
date: 2010-04-16
forum: General Help
---

### Post by Joshmcneel on 2010-04-16
I'm in deep. I'm very new to the whole Linux thing, and so i've been experimenting with Ubuntu for the past week or so. Well today I decided that I couldn't wait for the offical release of 10.04 LTS, so I upgraded from 9.10 to 10.04 LTS Beta 2. After realizing that many problems had come with that update, I decided to just format my Ubuntu partition and reinstall it. Somehow my GRUB stopped working from when I formatted Ubuntu, so I whipped out the old Toshiba recovery disk for Windows Vista 32bit. After many attempts to have the recovery portion of the disk fix all of my problems and seeing no results, I decided that reinstalling Ubuntu (and GRUB) might make everything all better. Well it didn't. Grub shows my Windows partition but fails to boot it. After selecting it, it goes to a blank screen and stops responding. And to add to all of my problems, my BIOS has changed slightly. It no longer shows/or responds to F2 or F12 when I tried to give another try at that Toshiba recovery disk. That kinda sucks since I can't choose what to boot. Please help me!! I really don't want to have to format my entire hard drive and try to install Windows Vista again (Not that Vista is anything anyone should love) I have many expensive programs that can only be activated a certain amount of times. I don't even think that I could reinstall Vista since my BIOS won't let me boot the CD/DVD drive.
Please help!

---

### Post by garvinrick4 on 2010-04-16
Here is a link on how to fix ubuntu and windows boot.

Always leave your BIOS to boot CD first, USB second if there is one and HD 3rd and you
will never get in a bind about fixing a problem with a recovery disk in Windows or ubuntu.

When you install ubuntu in the last page there is an advanced tab make sure it always says
installing grub in sda if that is drive you are using main HD. Not sda1.

When you get ubuntu grub fix do not forget when you boot it to do a CODE:

sudo update-grub



Read this will tell you how.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Joshmcneel on 2010-04-16
Well I tried the first thing on the link, which I guess isn't what you were talking about since for some reason it crashed GRUB. I had more difficulties with my BIOS not letting me choose what to boot, but somehow it lets me do it now, so I changed my Default boot order to CD, FDD, HD, then LAN. My only problem now is trying to get windows to start after I select it in GRUB. 

On the link you suggested there was a totorial on restoring Vista/Win 7's boot loader. Is that what you were wanting me to do?

Should I update GRUB to version 2?

---

### Post by garvinrick4 on 2010-04-16
Yes if you want to boot into Windows. Did you reinstall grub to sda and then sudo update-grub. Then try to boot into Windows.
 If that did not work then put in your windows recovery disk or its install disk go to windows recovery go to command line and put in the 2 lines of code in link and you will be
able to boot into Windows.

---

### Post by Native Dialect on 2010-04-16
Classic problem. When you installed Ubuntu onto your system, it was most likely set to place the GRUB loader on the Windows partition, thus replacing the Windows MBR. Unfortunately, the files to executing GRUB, would have been on your Ubuntu partition. By formatting that partition, you compromised GRUB's ability to function. Your Windows partition should be fine. 

Make sure that your BIOS is set to read the disc drive first. Run your Windows disc. From here, I will just link you to an article that explains how to replace/repair your Master Boot Record. 

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Follow those instructions and your computer will go back to booting only Windows. From there, you can use Windows Vista's drive shrink tool to format your Ubuntu partition. You can either blank it out entirely or return it to being part of your main Windows' partition. If you are unfamiliar with the partition tool in Windows Vista, press Windows Button+R, to open up the run tool. Type in diskmgmt.msc. Press enter, and you should see the disk management tool menu. From there, you can right click on the partition and take the appropriate actions. Best of luck.

---

### Post by Joshmcneel on 2010-04-16
Okay. I used command to fix the MBR. Windows boots fine. :) that was my main goal. It overrun GRUB though so i cant access Ubuntu now, but i assume that i can just reinstall Ubuntu and everything will be fine? Thanks for all of the help! : D

---

### Post by Native Dialect on 2010-04-16
You are very welcome. I had that same problem three years ago, and it nearly made me give up on Ubuntu. So I am glad that my experience can help others. In this case, I can help you.

And yes, your Ubuntu partition should not be accessible at this point, since you replaced GRUB with the original Windows Master Boot Record. You can format the Ubuntu partition and try reinstalling Ubuntu. You can install it and have Ubuntu write over itself. Or you can use Windows' volume shrink feature, via disk management, and simply wipe that partition away entirely. The choice is yours. To help you out some, I will refer you to this lovely help article

[How to Install GRUB to Different Partitions]("http://www.gnu.org/software/grub/manual/grub.html")

Scroll down to section 3.2 on the list. It will tell you how to install GRUB without having it write over your MBR. Good luck.

---

### Post by Joshmcneel on 2010-04-17
Thanks! I'm definitely going to keep what I did to fix it in my records in case it ever happens again. :) And thanks about the Grub/MBR suggestion, but I think i'm going to retire from trying to do anything to my computer that I don't fully understand until I can understand exactly what I'm doing. Thanks Again!

---

