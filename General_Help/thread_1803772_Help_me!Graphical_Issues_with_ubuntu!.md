---
title: "Help me!Graphical Issues with ubuntu!"
date: 2011-07-13
forum: General Help
---

### Post by RavCorp on 2011-07-13
Ok guys am having problems. When i first turn on my computer i start ubuntu!I login and my mouse icon is like blue and looks all missed up if i click on a program it turns all different colors.(See the attachment picture!)I installed Ubuntu along side windows.
But when i Start the computer the first time and run windows.Restart and boot from ubuntu
All works fine.

System Specs.
Memory 2.0GiB
Processor: Intel(R) Pentium (R) 4 CPU 2.00Ghz

Ubuntu Info
Ubuntu 11.04(natty)
Kernel Linux 2.6.38-10-generic
Gnome 2.32.1

Graphics card
Radeon 9250
(am not sure how to install this if its an .exe. I dont even know if it is installed help me!)

---

### Post by Mark Phelps on 2011-07-14
Sorry, but that model Radeon is a really OLD version -- and AMD dropped Linux driver support for it years ago.  In most cases, the default open-source drivers work OK.

If you didn't mess with the video drivers, and the screen display is OK in MS Windows, then basically, you're simply out of luck -- because there are no other drivers for that card.

---

### Post by Snowboi on 2011-07-14
Can you give me the output for 

```
lspci -nn | grep VGA
```

---

### Post by RavCorp on 2011-07-14
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

---

### Post by gandaran on 2011-07-14
hi,
which ubuntu release do you have? I had the same video card when I used ubuntu 10.10 and it worked fine then but wouldn't run unity so if you are using ubuntu 11.04 + unity try the ubuntu classic mode, should work well.

---

### Post by RavCorp on 2011-07-14
How do i check if i have it with unity

---

### Post by wildmanne39 on 2011-07-14
> **RavCorp said:**
> How do i check if i have it with unityHi, run this command in a terminal and it will tell you what release you are using.
```
lsb_release -a
```

---

### Post by RavCorp on 2011-07-15
> **wildmanne39 said:**
> Hi, run this command in a terminal and it will tell you what release you are using.
```
lsb_release -a
``` 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

thats what i got

---

### Post by wildmanne39 on 2011-07-15
> **RavCorp said:**
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

thats what i gotHi, this version has unity, at the login screen click on your username then go to the bottom of the screen and choose ubuntu classic with no effects and see if that works for you.

---

