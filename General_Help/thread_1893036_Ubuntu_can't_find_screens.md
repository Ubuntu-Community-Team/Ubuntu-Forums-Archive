---
title: "Ubuntu can't find screens"
date: 2011-12-09
forum: General Help
---

### Post by jdc.84 on 2011-12-09
Hi, only my second issue so far with Ubuntu this time around so things are looking up :)


I have 11.10 installed

_Here are the system specs from system info:_
Mem 3.9Gib
processor intel core 2 duo CPU E6750 @ 2.66GHz x 2
Graphics Unknown
OS Type 32-bit
Disk 93.7GB


_The Problem:_
I have just dual installed Ubuntu onto this machine with winXP pro.
In Windows i simply plugged my second screen in and away it went.
For some reason i can't do this on ubuntu.

I am assuming that it is a driver issue. However i don't really know where to begin and would really love some help.

What questions should i be asking to get this solved? And rather what is needed to be able to have to screens running side by side (not mirrored) on ubuntu 11.10?

---

### Post by gennatolls on 2011-12-09
First you need to find our some information about your graphics card.  It is most likely a driver problem.

Open up a terminal (ctl+alt+t):
```
lspci | grep VGA

```

That should give you what kind of card your running. For more info check out the official documentation [here]("https://help.ubuntu.com/community/BinaryDriverHowto")

Also have you installed additional drivers? It usually will install a recommend graphics driver.
If not,  Open System Settings-->Additional Drivers.
That should show you which graphics driver to get. If its Nvidia, it will install the X Server for Nvidia, and you can configure your monitors from within that app. I can't speak for other graphics cards, I only run Nvidia.

Good Luck

---

### Post by jdc.84 on 2011-12-11
Appologies. I was sure i marked this thread to email me when a response came in, however i never got it.

Erm.. things went from one screen to worse yesterday. I installed compiz control panel, changed a setting but now i cannot even see the task launcher or even the clock at the top of the screen! As i have my computer dual booting i have just switched back to windows. Tomorrow evening i will reinstall ubuntu and try again, it takes quite a while.

I am assuming that this new problem might be down to incorrect screen driver too

---

### Post by Mark Phelps on 2011-12-12
You don't have to reinstall Ubuntu, but what you need to do is follow the advice provided here and not go thrashing around installing stuff.

To restore Unity and ccsm, you will have to follow the details in the link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

However, if you can't even get a screen, then boot into Ubuntu using the LiveCD, and follow the directions earlier to get the video card information.

---

### Post by jdc.84 on 2011-12-12
Hmm ok cool thanks a lot. I'm assuming compiz control manager is ccsm. All i tried to do was enable the cube option.

Theres not another single program installed yet ha!

I will follow your advice this evening though. Thanks again ;-)

---

### Post by arubislander on 2011-12-12
Installing the Desktop Cube disables the Unity plugin. The Unity plugin is your Desktop interface that provides all the stuff that went missing. It is possible to have Unity and Cube enabled, but the process is fiddly and experience is not very satisfying.

---

