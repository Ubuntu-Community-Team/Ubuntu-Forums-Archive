---
title: "imageclass D420 Printer not working! HELP!"
date: 2012-02-25
forum: General Help
---

### Post by coronalove on 2012-02-25
Okay, so I downloaded the printer drivers from the canon website for linux. Now I have no idea what to do from here.. Somebody please help me, I am new to linux! I need to get this printer working.. canon imageclass D420

---

### Post by ajgreeny on 2012-02-25
What actual files did you download?  If it is an archive of some sort, eg .tar.gz, double click on it to see what it contains, or extract it with archive manager and then come back with a list of the files.

---

### Post by coronalove on 2012-02-25
In my firefox after I extract the download it says 

Linux_UFRII_PrinterDriver_V240_us_EN.tar.gz

I double click into that > another double click > then a list of files Documents, 64-bit_driver, Sources, 32-bit_Driver > 64-bit_driver (i clicked into here because my system is a 64-bit) > then it shows a folder that says RPM > then it shows these files

cndrvcups-common-2.40-2.x86_64.rpm
cndrvcups-ufr2-us-2.40-2.x86_64.rpm

oh yeaah! and im running ubuntu 11.10

---

### Post by ajgreeny on 2012-02-25
It looks as if you may have downloaded the wrong archive.  What you have is not for Ubuntu but distros that use the .rpm packages, eg Fedora, Suse, and many others.  Try again to see if there is an archive that specifies .deb files instead of .rpm files.

If there is no alternative archive available you can try using of alien, which can make some rpm packages usable in ubuntu, but I have never used it so can not help further with that.  It also looks as if there is a source code folder in the archive which may be helpful if you're prepared to compile your own packages, but again this is something I have never done, so can not really help you further apart from pointing you to [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by bjtuna on 2012-04-16
I ran alien on those RPM's, installed them, and managed to install the printer off those drivers. But there's a missing filter or something; it won't print.

Edit: it looks like Canon deliberately left the 64 bit Debian installation package out of their driver distribution. I think this is a really bad sign.  If you go into the Documents/ directory there's a Readme .txt file that is chock full of bugs, but none of them seem to say anything specific about why there is no package for 64 bit debian.

---

### Post by bjtuna on 2012-04-25
In case anyone needs it, I found the solution and posted it in another thread:

[http://ubuntuforums.org/showpost.php?p=11871878&postcount=80](http://ubuntuforums.org/showpost.php?p=11871878&postcount=80)

---

