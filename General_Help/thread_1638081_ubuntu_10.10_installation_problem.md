---
title: "ubuntu 10.10 installation problem"
date: 2010-12-05
forum: General Help
---

### Post by MFak on 2010-12-05
Hello to everybody out there. I am facing some difficulties with 10.10 installation for 32bit system. I have tried with cd and bootable usb too. I downloaded the version by ubuntu.com and burnt 3 different cds in order to succeed but failed. I also have created a separate partition for ubuntu (20 gb and 4 gb swap). Every time the installation began ok, i saw the ubuntu logo, then background wallpaper for 10.10 version appeared, mouse arrow could be moved around and after 1-2 minutes or cd stopped running or usb stopped being read. I left it for about 1-2 hours for a couple of times but nothing happened. Background continued it's appearance and that's alll, no message nothing. Tried also to installa 10.04 or google os but nothing seems to happen. Maybe installation versions have some problems finding specific hardware devices for driver installation? Please help me i am desparate.

---

### Post by Habeouscorpus on 2010-12-05
Have you booted successfully from a Live disk before on that computer? Sometimes the hardware just doesn't like it.

---

### Post by MFak on 2010-12-05
No never it is the first time i am trying to install ubuntu os.

---

### Post by Habeouscorpus on 2010-12-05
Could this be helpful?

[http://www.linuxine.com/story/ubuntu-1010-maverick-meerkat-usb-install-problems](http://www.linuxine.com/story/ubuntu-1010-maverick-meerkat-usb-install-problems)

---

### Post by ianhoolihan on 2010-12-05
Hi MFak,

I'm a complete novice to Ubuntu, but I had similar problems when I installed. It turned out that everything was fine, except the drivers for my graphics weren't suitable. Anyway if you hit spacebar when the keyboard/little man screen comes up, then F6 and select "nomodeset" then mine ran fine (this somehow does something to avert the graphics driver problem). You can then go along and install Ubuntu as per usual.

Note that the first time you try and run Ubuntu, you will have the same problem unless you run it in "nomodeset"...see [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132). Once you're in, just make sure you update the drivers (Ubuntu should detect this automatically), and you should be set!

PS, I only got this working yesterday, so no promises!

Cheers

---

