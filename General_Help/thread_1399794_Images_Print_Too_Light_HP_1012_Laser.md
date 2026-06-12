---
title: "Images Print Too Light HP 1012 Laser"
date: 2010-02-06
forum: General Help
---

### Post by Mel Thompson on 2010-02-06
Text prints excellently and boldly.  But whenever I go to print a graphic image, it comes out totally faded, blurry, almost unreadable when it comes to maps.  I have an HP 1012 Laser and am running Ubuntu 9.10, although this applied to all previous versions of Ubuntu and all other machines.  I am wanting to print images to mail them to friends without computers, but can only get text to be presentable.  Searched forums and saw an old, closed thread on this problem, however there had been no response to that one.  Tried going into system> administration > printing and setting for highest resolution, but to no avail.  Toner is still fine and printing all text material as sharp as ever.  If I hook up a Mac or Windows system, images print dark and bold and sharp.

---

### Post by dulrich on 2010-02-18
I'm still pretty new to Ubuntu, but I do think I have a solution to your problem. I had the same situation happen with my install. After searching, I finally found the following site:

[URL="http://hplipopensource.com/hplip-web/install/install/index.html"]http://hplipopensource.com/hplip-web/install/install/index.html
[/URL]
You may have the hplip package already installed on your system (I did).  But I found that downloading and following the instructions on this page fixed my problem. Hopefully it works for you.

BTW, there is a point in the script where it asks whether you want to reboot or simply unplug the printer. I had to do the reboot in order for the program to find my printer. The command in terminal after the reboot is 

```

sudo hp-setup

```Good luck!

---

