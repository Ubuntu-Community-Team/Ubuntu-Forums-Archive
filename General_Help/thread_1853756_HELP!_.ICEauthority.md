---
title: "HELP! .ICEauthority"
date: 2011-10-02
forum: General Help
---

### Post by dayoldmilk on 2011-10-02
Hi all,

Alright. Im a noob, but I got ubuntu. I love it. I downloaded xscreensaver, ran it, and ddeleted the one that came with ubuntu because it was interfering with the screensaver. My computer suspended and when I restarted it, I got a funky old windows 98-looking login screen and a message saying the .ICEauthority file couldnt update. Ive researched it and tried numerous lines in the terminal and it wont work. Worse yet, I dont know how to reinstall ubuntu seeing as GRUB overwrote the windows bootmanager, and I dont have a W7 disk to repair the bootmanager, H E L P ! ....anyone!?

---

### Post by dayoldmilk on 2011-10-02
bump help someone?

---

### Post by dayoldmilk on 2011-10-02
Heeeeeeeeelllllllllppppppppppppp plllllllleeeeeeaaaaaasssssseeeeeeee

---

### Post by bodhi.zazen on 2011-10-03
> **dayoldmilk said:**
> Hi all,

Alright. Im a noob, but I got ubuntu. I love it. I downloaded xscreensaver, ran it, and ddeleted the one that came with ubuntu because it was interfering with the screensaver. My computer suspended and when I restarted it, I got a funky old windows 98-looking login screen and a message saying the .ICEauthority file couldnt update. Ive researched it and tried numerous lines in the terminal and it wont work. Worse yet, I dont know how to reinstall ubuntu seeing as GRUB overwrote the windows bootmanager, and I dont have a W7 disk to repair the bootmanager, H E L P ! ....anyone!?

Well, first, don't panic.

Second, please do not bump your threads in anything less then 24 hours.

Third, slow down. What does a screensaver have to do with .ICEauthority, and what does grub have to do with installing Ubuntu ?

to resolve your .ICEauthority problem , boot to recovery mode, drop to a root shell. You will not have a graphical interface, but you will be logged in as root.

Simply run ```
chown -R your_user:your_user ~your_user
```

And reboot.

---

### Post by dayoldmilk on 2011-10-03
Thanks for replying. Sorry, this is a brand-new computer (and right now my ONLY computer to use) and I am not really knowledgeable when it comes to this thing, (yet hopefully...). well, I did that and:

chown: cannot access '/home/dylan/./gvfs': permission denied
chown: cannot access '/home/dylan/../dylan/gvfs': permission denied
chown: cannot access '/home/dylan/.gvfs: permission denied

:(

by the way, to even use my computer I have to type
unity --reset

which gives me windows 98 graphics, and I cant use my right click, or click on some buttons or apps. 

thanks!!

could it have been something I deleted..? if so Ill gladly give the history... anything you need to ask ill tell ya :o

---

### Post by bodhi.zazen on 2011-10-03
> **dayoldmilk said:**
> Thanks for replying. Sorry, this is a brand-new computer (and right now my ONLY computer to use) and I am not really knowledgeable when it comes to this thing, (yet hopefully...). well, I did that and:

chown: cannot access '/home/dylan/./gvfs': permission denied
chown: cannot access '/home/dylan/../dylan/gvfs': permission denied
chown: cannot access '/home/dylan/.gvfs: permission denied

:(

by the way, to even use my computer I have to type
unity --reset

which gives me windows 98 graphics, and I cant use my right click, or click on some buttons or apps. 

thanks!!

could it have been something I deleted..? if so Ill gladly give the history... anything you need to ask ill tell ya :o

I have no idea what "windows 98 graphics" might be (Ubuntu does not have anything to do with windows 98) or what you might have done to your system. Did you delete things in your home directory ? Usually your initial .ICEauthority error is due to running graphical applications as root (you should use gksu).

Perhaps if you can tell us what you did and give a better description of the problem then "windows 98" we could help.

---

### Post by dayoldmilk on 2011-10-03
Sorry about the confusion, I meant like the windows were squared and everything was grey and blue, how it used to look on old versions of windows, not windows itself...

I installed a package from the Ubuntu Software Centre, called "xscreensaver'.
There was a bug that made the two screensaver packages not work properly when both were present, so I deleted the one that I didnt want, (the one it came with).

---

### Post by bodhi.zazen on 2011-10-03
Sounds as if you are having a problem with Unity, I am not really sure.

installing xscreensaver should not have caused these problems, and a title "HELP! .ICEauthority" is unlikely to draw attention.

I suggest you start a new thread, tell us what you have done (again I suspect you have been running things as root or at least that installing xscreensaver is not the only change you made) and include a screenshot.

Be sure to tell us what video card you have.

---

### Post by glyphted on 2011-10-04
It sounds like you just started your Ubuntu Voyage, and you don't have any important files located in Ubuntu. Your BIOS settings/order can still be reached, if looking to reinstall Ubuntu. These are hard-installed and can be reached by pressing the keys specific to your brand of computer. ([http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)) You need to acquire your bootable USB/CD. Go to your windows partition, right click "my computer" and select manage, then select disc management. Delete volume on the partitions that Ubuntu occupied, ONLY these. Shut your computer down, press the key, and reinstall Ubuntu via bootable USB/CD. Hope this helps!

---

### Post by dFlyer on 2011-10-04
First Welcome to Linux. Now when you say you deleted the screen saver how did you do that. Did you just search for the files and delete them or did you uninstall them using apt-get or synaptic or another package manager?

---

### Post by dayoldmilk on 2011-10-04
thank you glyphted, thats exactly what i was lookin for! it worked and now im back on ubuntu :) thank you so much!!

---

