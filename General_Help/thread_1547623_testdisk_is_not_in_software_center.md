---
title: "testdisk is not in software center"
date: 2010-08-07
forum: General Help
---

### Post by opetrenko on 2010-08-07
tried to install ubuntu 10.04 next to XP. 
lost xp and no ubuntu. lost "loader"(?)
back to livecd, deleted ubuntu partition with gparted, with intent to reinstall, but learned there is a loader that might be fixed.

But undeleting partition requires testdisk
load livecd to run it, but cant find it in software center. 
[here]("http://ubuntuforums.org/showthread.php?t=1138114") it was suggested to type

sudo apt-get update

whatever this spell does, testdisk still can't be found in the software center

How and where to get this program?

Thank you

---

### Post by clhsharky on 2010-08-07
opetrenko

> How and where to get this program?
Use Synaptic package manager, search testdisk.

Sharky

---

### Post by darolu on 2010-08-07
Try installing it from the terminal, go to Applications->Accessories->Terminal:
```
sudo apt-get update
sudo apt-get install testdisk
```

You need to run testdisk from the terminal anyways; if installing this way fails try with this link: [http://packages.ubuntu.com/lucid/testdisk](http://packages.ubuntu.com/lucid/testdisk)

---

### Post by wilee-nilee on 2010-08-07
I believe the universe repository is where it's at.

---

### Post by opetrenko on 2010-08-07
Everybody, thank you for the amazingly prompt replies!

[clhsharky]("http://wwww.ubuntuforums.org/member.php?u=543156"), search "testdisk" returned 0 results

[darolu]("http://wwww.ubuntuforums.org/member.php?u=436585"), last line returned "E: Couldn't find package testdisk"

[wilee-nilee]("http://wwww.ubuntuforums.org/member.php?u=906928"), turned on the universe repository and still couldn't find the testdisk in Synaptic Package Center. Ran all updates in it. As result, something wrong with window window manager now: no top row, many items are not responding to mouse clicks, menus don't work. I am so glad I'm running from liveCD and can try again. 

Please, help me to get testdisk so I can eventually get my XP back. 
Thank you!

P.S. Would you add a bit more expanded replies for the total noob.  
P.S.S. I'm running/installing ubuntu 10.04 desktop that I've downloaded a couple of days ago.

---

### Post by cpmman on 2010-08-07
Applications - Ubuntu Software Centre - testdisk

edit: UK mirror & all repositories enabled.

---

### Post by aysiu on 2010-08-07
> **wilee-nilee said:**
> I believe the universe repository is where it's at.
Yes, before you can do ```
sudo apt-get update && sudo apt-get install testdisk
``` or use Ubuntu Software Center or Synaptic Package Manager to install *testdisk*, you have to make sure you have the Universe repositories enabled.

First, go to System > Administration > Software Sources

Check all the boxes up top, especially the one marked **Universe**. Then click **Close**. When prompted, click **Reload**. It should then appear in Synaptic.

---

### Post by xXxBlender3DxXx on 2010-08-07
Just download the binary: [http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2"), extract it, right click on the testdisk/photorec binary and make it executable.

Then, just cd to the directory with Terminal and run it.

---

### Post by opetrenko on 2010-08-07
Everybody, thank you !
aysiu, your solution worked! 

P.S. doesn't want to recover the deleted partition, though. But that's whole other story. Will study forums first. 

again, THANKS!

---

