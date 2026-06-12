---
title: "Wubi virus"
date: 2012-08-15
forum: General Help
---

### Post by subzul on 2012-08-15
Hi!

I am new in the linux world. I was using windows as long as i can remember, but for the past month i only had problems with it. So i decided give linux (Ubuntu) a try through wubi (since i dont have enough knowledge about partitions). I understand almost everything. But i have question about viruses. I know they cant be used in wubi, but if i download any can they execute themselves in windows without me knowing it? I mean if i download virus but i never execute the program that contains it in windows and never even boot windows can they still be threat to it?

---

### Post by Mark Phelps on 2012-08-15
IF you download a virus file and save it in your Linux filesystem, MS Windows can't see it, so it won't do anything.

IF you save it in the Windows filesystem, then MS Windows CAN see it, and could possibly get infected from it when you then run Windows.

---

### Post by subzul on 2012-08-15
So, let me recap. If i download file that contains virus to wubi (and possibly run it) it will have no effect on my windows 7, right?

---

### Post by Frogs Hair on 2012-08-15
Correct , If look in the Ubuntu home folder , File System > Host is the link to the Windows file system In a Wubi installation. Unless you manually move the infected file from Ubuntu into Host, Windows can not be infected.

---

### Post by subzul on 2012-08-15
Thanks, will give wubi a try tomorrow.

---

### Post by Petro Dawg on 2012-08-15
1st, don't worry about accidentally giving your windows system a virus through wubi install.  I doubt there are any viruses out there that would be able to execute all the necessary steps required to "jump" from linux to windows with out you helping it along.  I expect if you downloaded a virus ridden windows compatible program onto a usb drive while using linux and then used that drive/program in windows it would be possible to spread the virus.  Of course, you could just use an anti-virus program to scan the usb drive before using it on windows again if you are concerned you downloaded mal-ware.

> ...  So i decided give linux (Ubuntu) a try through wubi (since i dont have enough knowledge about partitions)...

2nd, you do not need to know anything about partitions to do a full install of Ubuntu.  The installation disk will handle all that stuff and is pretty straight forward unless you want to set up a dual boot with windows and Ubuntu.    If you are ready to ditch windows completely, just download an Ubuntu install CD and do a complete install.  There are plenty of online tuturials showing you how to make an install CD from an ISO image.

It is my understanding that wubi installations can become slower over time since they are subject to hard drive fragmentation issues from the windows operating system.  So you are really better off eventually going to a full install, or dual boot (if you ever get confident enough with partitions).

---

### Post by subzul on 2012-08-15
Well, i plan to give my PC full installation (and ditch windows completely), but i want to see how it really works before i do that and wubi is better for that (i think). Also i plan to test it for a week maybe so wubi is probably better because it is easier to use (install and uninstall when finished).

---

