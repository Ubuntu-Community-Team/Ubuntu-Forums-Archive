---
title: "Migrating from windows 7 pro"
date: 2011-04-24
forum: General Help
---

### Post by goodiesguy on 2011-04-24
OK, so today i've decided to change completely to ubuntu from windows 7.

At the moment i have ubuntu installed in which i can go into my windows 7 ad and remove programs and get rid of it.

How can i copy all my files over to ubuntu, then get rid of windows 7 and let ubuntu take over the rest of my hard drive?

Also, i have WINE installed on my ubuntu, and i would like to know if their is a list of compatible software that will work with it.

Sorry if this post is in the wrong place, but im new and im really looking forward to being a ubuntu user.

oh, the computer in question is a compaq presario c302TU (C300) laptop with 1gb ram, 40gb hard drive.

---

### Post by ghostborg on 2011-04-24
[http://youonpictures.com/?p=171]("http://youonpictures.com/?p=171")
I think that is what you want.
Also check out ntfs-config in the synaptic package manager.

You might find Virtualbox a better way to run Windows programs in the future if you get a system with a larger hardrive and more memory.

Wine [http://www.winehq.org/]("http://www.winehq.org/")

App database [http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by wilee-nilee on 2011-04-24
> **ghostborg said:**
> [http://youonpictures.com/?p=171]("http://youonpictures.com/?p=171")
I think that is what you want.
Also check out ntfs-config in the synaptic package manager.

You might find Virtualbox a better way to run Windows programs in the future if you get a system with a larger hardrive and more memory.

Wine [http://www.winehq.org/]("http://www.winehq.org/")

App database [http://appdb.winehq.org/]("http://appdb.winehq.org/")

Your first link is for a wubi install.

---

### Post by coldraven on 2011-04-24
Buy an external USB drive, they are cheap! Then backup your files!!!!

---

### Post by Vaphell on 2011-04-24
don't get rid of win7 completely yet, especially if you paid for it :) You may need it in future, when you hit some serious roadblock while having a brutal deadline or when you just want to play some brand new shiny game that won't work with wine. Imo dual boot is the way to go.

---

### Post by bollix47 on 2011-04-24
> How can i copy all my files over to ubuntu, then get rid of windows 7 and let ubuntu take over the rest of my hard drive?

You can do the copy part using Nautilus File Manager from within ubuntu.

To add Nautilus to your top panel right click on a blank bit and select "Add to Panel", then select "Custom Application Launcher".  In the name field enter something descriptive like File Manager and for the command type nautilus.  Should produce a shell icon.

Open Nautilus by clicking the icon once.

Once open there should be an entry for your Windows partition on the left side, something like ## GB Filesystem.  You can click that entry and navigate to the areas you want to copy, highlite the files (maybe click on edit and select all), click on edit and select copy.

You can open another instance of Nautilus and navigate to where you want to paste the files and right-click paste.

---

### Post by Frogs Hair on 2011-04-24
Keep Windows and dual boot you may need it as stated already . Wine is a great tool , but it has limitations. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by walt.smith1960 on 2011-04-24
> **Vaphell said:**
> don't get rid of win7 completely yet, especially if you paid for it :) You may need it in future, when you hit some serious roadblock while having a brutal deadline or when you just want to play some brand new shiny game that won't work with wine. Imo dual boot is the way to go.

Excellent suggestion.  Let's say you buy a new piece of hardware and it doesn't work under Linux. Is it faulty hardware or a software problem?  You call the technical support phone number.  The first question is likely to be "What version of Windows are you using?"  If you answer "I don't use Windows, I use Linux" you will likely receive a reply like "I'm sorry, we don't support Linux" <click>.  If the device works with Windows (aren't you glad you have a rarely used Windows install?) then it's a Linux issue.  If it doesn't work in Windows, it's likely a faulty device.

---

### Post by Mark Phelps on 2011-04-25
Your comments are contradicting ...

> **goodiesguy said:**
> At the moment i have ubuntu installed in which i can go into my windows 7 ad and remove programs and get rid of it..
The only way you can remove Ubuntu from inside Windows like "remove programs" is if you installed it using Wubi -- and in that case, removing Windows removes Ubuntu as well.

> Also, i have WINE installed on my ubuntu, and i would like to know if their is a list of compatible software that will work with it.
It doesn't make sense to have Wubi AND Wine.  So, this reads like you have Ubuntu installed in its own partition.

Without knowing which is the case, it's hard to provide detailed advice.

---

