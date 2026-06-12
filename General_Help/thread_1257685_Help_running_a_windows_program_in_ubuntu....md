---
title: "Help running a windows program in ubuntu..."
date: 2009-09-04
forum: General Help
---

### Post by yescdr on 2009-09-04
Hi,
 I'm very new to Ubuntu, I own a small business and I want to switch from windows xp to ubuntu permanently, for obvious reasons. Ubuntu is way better! 

I have encountered a problem installing my Inflow Inventory program, which I use often use in xp, I have tried using the wine application but it wont even launch the program after the install. I thought this might have something to do with the .Net Framework it needs to install, So I did a code I found in the forum here is the code : 
[B]
How to: install .net framework 2.0 in ubuntu using wine[/B]                                                                             1- set Windows 2000 as your default app in wine config.

2- In teminal enter these lines one by one:
     Code:
     wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) 
     Code:
     sh winetricks corefonts dotnet20 
     Code:
     sh winetricks fakeie6 
It said it installed successfully, YAY I thought, when I tried to run the program again this time I got 2 runtime errors. 

Runtime ERROR Program: C:\windows\Microsoft.Net\Framework\v2.050727\mscorsvw.exe
R6034
an application has made a attempt to load C Runtime Library incorrectly

Runtime ERROR Program: C:\program files\inflow inventory\inflow.exe
R6034
an application has made a attempt to load C Runtime Library incorrectly

Also this error occurred: C:\windows\Microsoft.Net\Framework\v2.050727\mscorwks.dll could not be loaded
Any Help would be greatly appreciated.

---

### Post by P4man on 2009-09-04
Not sure. You could run ./winetricks and try some of the other tricks, like installing mfc42 and mdac, but to be honest, I dont think this is a good idea. If inflow is critical to your business (and I guess it is), you don't want to run it with wine. Its just not stable or reliable enough for critical apps.

Either find a solution that is native to linux, or stick with windows, or run windows and inflow  in a virtual machine ([https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)).

---

### Post by blackened on 2009-09-04
> **P4man said:**
> ..Either find a solution that is native to linux, or stick with windows, or run windows and inflow  in a virtual machine ([https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)).

I second this suggestion. Whether or not a virtual machine would benefit you depends on how often you use the inventory software. If you run it very often or all the time, then you're better off just running it on Windows.

There may be a piece of Linux native software that suits your needs just fine. You should look into that as a starting point.

---

### Post by P4man on 2009-09-04
If you're looking for a native solution, perhaps check this out:

[http://www.openerp.com](http://www.openerp.com)

If I understand it right, its free, but you can purchase it if you want support. It has an online demo that may give you a clue as to whether or nor it serves your needs.

Then again, unless this is just a small part of your business, picking an ERP to run on your OS of choice is kinda of like .. backwards. Its the software that matters most, then pick an OS it runs on. If inflow works well for you, switching to something else just because it runs on linux is not likely a good strategy.

---

### Post by yescdr on 2009-09-04
Thanks for the very quick replies, I first tried the Lemon program from the add and remove programs button, I thought it would be good, but can't set it up either due to a sql problem.  I think I would still rather try to get some program for ubuntu. Mainly because I haven't yet had any problems with ubuntu like I do windows. 

I also tried the openerp but also had a problem with the sql. 

I have also looked into installing a virtual windows on ubuntu, I was thinking about doing it but wasn't sure how stable it would be?   I only use the program a few times a day, not constantly.

---

### Post by The Thug on 2009-09-04
I've installed VirtualBox on Ubuntu and am running XP inside the VB.

Works perfectly and haven't had any hassles

---

### Post by ianmillington on 2009-09-04
I agree with the others here. So long as you have a Windows installation disk, install virtualbox and then install Windows within it. Your windows programs ought to install and run without issue. 

For example I run Dragon Naturally Speaking in a VM (although to be fair I've now got it running under Wine as well). Don't expect Games to run well though, especially those needing 3d.

Hope this helps

Ian

---

### Post by P4man on 2009-09-04
> **yescdr said:**
>  I was thinking about doing it but wasn't sure how stable it would be?   I only use the program a few times a day, not constantly.

Its certainly more stable than wine. In fact, its rocksolid. Virtualization is something often used on servers to consolidate multiple servers on to one physical machine. Its not experimental technology anymore, its used for mission and business critical apps. 

Of course, the windows you install on the VM, is still windows :) but if it only needs to run a couple of apps in a shielded environment, that should be good enough.

---

### Post by yescdr on 2009-09-04
Thanks a lot for all the help, I will install the virtual windows, as soon as a get a 95 or 98 cd all I have is xp upgrade. I'll post my results when I install it, and hope it goes well. 



Microsoft could learn much from ubuntu community :)
but all Microsoft thinks about is the money, not the people.  

Thanks again everyone.

---

### Post by yescdr on 2009-09-06
Hello, I have installed the Virtua lBox with windows xp pro, and installed Inflow. So everything is working great inside ubuntu.

Thanks, David

---

### Post by ianmillington on 2009-09-06
Great stuff!

---

