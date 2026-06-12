---
title: "How do I install Ubuntu from Dos?"
date: 2011-07-16
forum: General Help
---

### Post by thedave016 on 2011-07-16
So I have a Dell Precision 360 that was made in 2003.  Recently tried to reformat the hard drive to restore the original factory settings (Windows XP), and it made a glorious mess of things (output ghosterr.txt), so I thought that I would try Linux!  Trying to install Ubuntu, but I am completely locked out of Windows and am trying to load it from Dos... 

Burned the 700MB ubuntu file to a DVD-R.  Accessed the boot menu and tried to boot from "4: IDE CD-ROM Device", but it says that there is "no active partition".  I wonder if I just need to run the "wubi.exe" file from the A:\ prompt, but I have no idea how to make this work... Is it possible to load Ubuntu from Dos in my situation?  Thanks!

David

---

### Post by aysiu on 2011-07-16
Loading from DOS won't work.

When you try to boot from the CD-ROM device, are you absolutely certain your CD-ROM reader is broken? If it's not, it's possible you burned the Ubuntu .iso file incorrectly. First of all, the .iso should not be modified in any way (for example, if you have WinRar installed, WinRar may prompt you to extract the .iso). Secondly, the .iso needs to be burned as a disk image and not a data file and not a "bootable CD." If you pop the DVD into the computer you burned it on (I'm assuming it's not the one that boots only to DOS) and look at the contents, do you see a bunch of files and folders, or do you see one file?

---

### Post by coldraven on 2011-07-16
You must have burned the DVD on another computer, is that correct?
Are you sure that the computer you are trying to upgrade can read DVDs? It might only have a CD drive.

---

### Post by thedave016 on 2011-07-17
The Dell definitely can read DVD's from the CD-ROM drive, and i don't think that the CD-ROM drive is broken, rather the DVD that I burned may just be formatted incorrectly.  I burned the Ubuntu DVD from a MacBook Pro that is about 18-months old...

The Ubuntu file that I burned to the DVD was one folder with a series of icons such as: wubi.exe, usb-creator.exe, pool, pressed, readme.diskdefines, pics, md5sum.txt, isolinux, install, dists, casper, boot, and autorun, but actually now that you mention it, the ubuntu-11.04-desktop-i386.iso file was not burned to the DVD... Should I make a new one including that file as well?  How do I format the DVD correctly so that it will boot from the boot menu?

When I burn the DVD in Apple, you burn it right off Finder, and there appears to be no option to format the DVD in any specific way, even after I toggled a little bit with the "Disk Utility" options.  May be able to find out how to format it if I know what i'm trying to do.  Is there anything special that I have to do to burn the "iso" file as an image and not as a data file? 

Thanks very much for the assistance guys!  I really appreciate it!

---

### Post by Mr. Shannon on 2011-07-17
> The Ubuntu file that I burned to the DVD was one folder with a series of icons such as: wubi.exe, usb-creator.exe, pool, pressed, readme.diskdefines, pics, md5sum.txt, isolinux, install, dists, casper, boot, and autorun, but actually now that you mention it, the ubuntu-11.04-desktop-i386.iso file was not burned to the DVD... Should I make a new one including that file as well? How do I format the DVD correctly so that it will boot from the boot menu?

No, you want to burn ubuntu-11.04-desktop-i386.iso as an image, it will make a directory structure on the disk for you.  An .iso file is essentially an entire disk in a file.  For instructions on how to burn the .iso file with Mac OS X follow this link:  [http://hints.macworld.com/article.php?story=20060619181010389]("http://hints.macworld.com/article.php?story=20060619181010389")

---

### Post by thedave016 on 2011-07-17
Guys, it worked!  You know I was having these incredible system problems with Windows, but I just managed to successfully install Ubuntu, and from the first 10-minutes, everything seems to be working great!  You know I even had a major issue with a scrambled screen that the installation seems to have fixed, so I am more than pleased.  Its 1:15AM but all i want to do is stay up and explore a little bit.  

Anyways, thanks again for your help! 

David

---

