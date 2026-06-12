---
title: "printer type not recognized"
date: 2011-05-21
forum: General Help
---

### Post by Kgurl1775 on 2011-05-21
Ok, I am incredibly green here.  I am not great with computers in general, but I'm trying.  I have recently had linux installed on my computer, but my printer which is a Canon Pixma MP495 is not recognized when the computer searches for it.  The 395 is and the 500 is, but not the 495.  I need to know what to do.  I found a driver by canon which I downloaded.  It is sitting in the archive manager but I have no idea what to do with it now and how to get everything working!  Please use easy to understand non-computer person talk with me since I have no idea what I'm doing.  Forgive me for my ignorance but applaud me for my desire to learn :D  Thanks!
~Karen  
PS I DO know how to open a terminal, but after that...

---

### Post by BicyclerBoy on 2011-05-21
Check:
The canon driver is a debian linux package ? (.deb)..
The download will be a tar archive .tar.gz..

You can just open the archive, extract & then click on the .deb package..

Script method:
Some of the canon driver packages come with an install script "install.sh"
This script is a better method..(run from terminal ./install.sh with sudo)

Manual method:
It is nice to do this from terminal so you can see the result..
dpkg -iG cnijcommon....deb
dpkg -iG cnijfilter......deb
(you need to use sudo blah...)

32 bit problems:
One problem you may have is that the driver is 32bit & your install is 64 bit..
Then you need to use
dpkg -iG --force-architecture package.deb 

Other:
May need to logout/login to get CUPS to find the printer..

(dpkg -G option stops you installing older versions of files)

---

### Post by Kgurl1775 on 2011-05-23
Yahoo!  I did it!  Thank you so much for your great help :)
~Karen

---

