---
title: "Synaptic Help"
date: 2010-02-16
forum: General Help
---

### Post by LacedSpirits on 2010-02-16
I've been lucking here for awhile getting tips and tricks from you all.  I finally registered today because I have an issue that I can't seem to fix and I need some help.  Earlier today I was installing snort, acidlab, and acidlab base when half way through the installation, the package manager crashed. Now, everytime I try to open Synaptic Package Manager, I get this message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report"

Now I've searched my files for "configure-a" in "dpkg" folder with no luck.  As you can tell, I'm very new to linux.  I've had my Dell Mini10.1 w/Ubuntu for about 2 months and I've had to run the "System Restore Disk" twice already to fix problems like these.  I'm quite proficient with Windows so I'm not a complete moron but this Linux/Ubuntu is really tripping me up.  Any help or suggested reading would be greatly appreciated.  
Thanks,
McKenzie

---

### Post by howefield on 2010-02-16
Open a terminal, Applications > Accessories > Terminal and type the following into it

> sudo dpkg --configure -a

Enter your password when prompted.

---

### Post by 2hot6ft2 on 2010-02-16
Welcome to the forums LacedSpirits you can find even more information here
[http://help.ubuntu.com/](http://help.ubuntu.com/)

When you get bored or want to just look around the documentation and wikis.

---

### Post by 2hot6ft2 on 2010-02-16
howefield already answered the question.

I meant for when you can't find anything of interest in the forum

---

