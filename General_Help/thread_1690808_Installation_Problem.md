---
title: "Installation Problem"
date: 2011-02-19
forum: General Help
---

### Post by NexyPlays on 2011-02-19
I want to switch from Windows 7 (32-bit) to Ubuntu 10.10 (32-bit), but I can't install it on my PC for some reason.  I've tried burning the .iso onto 2 or 3 different DVD+ROM discs now, I keep getting the following message when I try to install it.
 
Message:
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
 
Does anyone know what I should do?
 
Thanks.

Edit:  I got it to work, I'm not sure if this actually made any  difference, but I formatted my hard drive using my Windows 7  installation DVD before trying to install Ubuntu 10.10.  But it worked  fine after that and I'm now running it on my PC without any problems (at  the moment).  Thanks for the help anyway guys!

---

### Post by Quackers on 2011-02-19
Welcome to UF.
Have you checked the md5sum of the downloaded iso file, to check that it is good?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, when booting from the dvd, when it gets to the first purple screen (the one with the little man icon at the bottom), press any key. Choose your language, then on the next screen choose the option to check the cd for defects.
If one error is found, it is one too many. Try burning the dvd again, using slow settings.

---

### Post by NexyPlays on 2011-02-19
No I haven't, how do I check it?
 
Edit:  I'll try burning it again using the slowest settings instead of the maximum, but how do I check the md5sum?

---

### Post by Quackers on 2011-02-19
Have a look at the link I posted, for details.
Alternatively you could first check the dvd with the above instructions. If the dvd checks out, the download is almost certainly good.

---

### Post by NexyPlays on 2011-02-19
It tells me how to check it using the terminal, but that's on Linux. I'm running windows 7 right now.
 
The iso I downloaded was right from the Ubuntu website, but I've used the disc to install it on a different computer, so I don't see why I would be having problems now?
 
Edit:  Okay, I right clicked the iso file and clicked burn image, but when I clicked verify it told me that the iso file is invalid.  Should I download it again?  And should I use a download manager of any kind to download it?

---

### Post by Quackers on 2011-02-19
If you've used the disc on other computers then it should be good. It could be a problem with the cd drive you are now using to read the disc. It's worth trying to clean the laser - carefully!

---

### Post by NexyPlays on 2011-02-19
How do I clean the laser?  What should I use to clean it?

Edit:  Wait no, I don't think it would be the cd drive, because I also tried to use a bootable usb drive and it didn't work either.  It gave me the same message as when I tried the dvd.

---

### Post by Quackers on 2011-02-19
I believe there are cleaners, but it may be worth just carefully wiping it with a soft, dry cloth. Don't press too hard though :-)

---

