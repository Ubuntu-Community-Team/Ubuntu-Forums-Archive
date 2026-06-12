---
title: "Ubuntu 12.04...freezing"
date: 2012-04-30
forum: General Help
---

### Post by meduser on 2012-04-30
Hello, I downloaded on the 26th the new LTS 12.04. I really like it and have found the dual monitors setup works perfectly. I am having some issues though.

1) Everytime I try to open Libre office, it freezes instantly. You don't even see any of the bar go across. I left it for 20 minutes the first time it happened, as I thought maybe first time setup issue. But no, everytime I start up Libre it freezes.

I also tried to start gimp just now, and it froze up. I have been having a lot of freezing issues since the new install. I did not upgrade, I installed fresh full LTS 12.04 64 bit. I have run apt-get update, apt-get upgrade, etc, and still have this issue. I am sure it is something little, just not familiar enough with Ubuntu to know what is wrong.

Any help is greatly appreciated, as I just started my practicum today to finish off University.

Thanks in advance.

Med

---

### Post by meduser on 2012-04-30
I find it is locking/ freezing when ever I open a new program. 

I have 12 gigs of ram, so ram is not an issue. It happens when I have nothing running, or a pile of things running. 

The mouse still moves, but I can't click on anything, and can't close anything.

---

### Post by carranty on 2012-04-30
Well, next time it freezes try going to the command line. Ctrl-Alt-F4 should bring up a black screen with a command line interface.  Login and run the command top, this will list (in descending order) the processes which are taking up the most processing power, if one is taking up a lot, try closing it.  You can do that by exiting top (by pressing q) and entering 

```
sudo kill PID
```replacing PID with the process number (the number in the left hand column of top.  It won't stop the same form happening again (I'm afraid I can't help you with that) but it'll hopefully stop you having to restart you r computer all the time.

By the way, how did you get dual monitors working?  Are you using separate x screens or twinview?

---

### Post by meduser on 2012-05-01
Thanks, I'll try that.

As far as the monitors go, I am using the nvidia software, and running one in twin view. Both monitors display different pages and such.

---

### Post by meduser on 2012-05-01
So it appears to be the Compiz software causing the issue. I just tried the top command, and Compiz was at the top of the list. I killed Compiz, and got my screens back, and everything is working again.


So, is anyone else having issues with compiz on Ubuntu 12.04 LTS?


Is there a way to check this out? I am freezing up (locked up except for the mouse can move, but can't click anywhere) whenever I open a program, I have Cairo dock, but the freeze happens with or without Cairo. I have the freeze from both Unity bar and Cairo dock. If I go into home folder, and find a pdf, and click to view it, I lock up.


I have to get this resolved...anyone please..what can I run to find out what the problems are. i think it is Compiz related.

---

### Post by SingingBush on 2012-05-01
I've had similar problems since upgrading. My machine has frozen up on me 3 times this evening and the only way to recover was to power off at the switch.

---

### Post by dmdelorme on 2012-05-01
I have my system freezing too mostly using Firefox I need to to a hard reset. No mouse or keyboard. I had this problem in beta 1 and into 2 now it has reappeared where do i go for more information after i reboot so i can submit a bug report... 
wonder if it is Compiz???

---

### Post by SingingBush on 2012-05-01
I did see in another thread something about latest Nvidia driver causing a problem. Are you also using 'nvidia-current'?

---

### Post by dmdelorme on 2012-05-01
No i have a Acer 5755 laptop i7 4g ram no special drivers. every thing works but dim and brightness keys reversed. it runs nice under Ubuntu except for the Freeze ups. i have 2 finger scrolling set up. i might disable that and see if it goes away.:confused:

---

### Post by SingingBush on 2012-05-01
If you mean the Acer Aspire 5755G, then that does have Nvidia GPU. It's the GeForce GT 540M. Are you sure the Nvidia driver is not installed?

---

### Post by dmdelorme on 2012-05-01
No G it is a 5755-9674 hard to read as i took all the stickers off the cover.
hardware and software environment is as follows

Ubuntu 12.04 - 64-bit  version - Intel® Core™ i7-2670QM Processor (6 MB L3 cache, 2.20 GHz,  DDR3 1600 MHz) - 6GB DDR3 SDRAM - 750GB hard drive - 15.6" HD Widescreen  CineCrystal™ LCD display (1366 x 768) - Intel® HD Graphics 3000 -  Intel® HM65 Express chipset - DVD±RW DL - webcam - 802.11b/g/n WLAN -  gigabit LAN - Bluetooth® - HDMI® - USB - Multi-in-1 card reader - 6-cell  battery

I have virtual box setup with Win 7 so i can watch Netflix Cr@p workaround but it works. but it was not running when this happens.
and i use the Unity interface as i have gotten to like it in its current form. It is much better then the first few iterations and Gnome 3 well it kinda sucks sorry guys it is just my opinion and i know many people like it. 
a little off topic but if your going to buy a laptop set up a boot key and try it on the lap top in the store it saves grief later and it is fun watching all the window machines panic when they reboot back to windows... If they wont let you go some place else or don't ask.

---

### Post by meduser on 2012-05-01
I was running the latest Nvidia driver, but I followed the post and went to a different one. 

I haven't frozen since, but we'll see.

---

### Post by meduser on 2012-05-02
Nope, still freezing when opening.

Programs that cause freezing when opened...

Libre Office
Gimp
Vuze
Gwenview



Programs not having issues:
Chromium
Chrome
Thunderbird
Firefox
Gedit
Geany


The programs causing the freezing freeze up everytime they are opened.

---

### Post by Zomaian on 2012-05-02
I have the exact same problem after I upgraded from 11.10 to 12.04. It's seems to be an issue with the NVIDIA X Server. Basically what happens is that the X Server randomly gets killed when intensive graphic related things are used like watching a Youtube video on Firefox or a film in VLC. I have also had the issue when I'm heavily multitasking or switching between programs quickly.

Either one of these three happen:

[LIST]
[*]Screen goes black and logs the currently logged in user out.
[*]Everything completely freezes.
[*]Everything freezes except for the mouse which I can move slowly.
[/LIST]
I have tried removing and reinstalling X Server but no luck. It's definitely a problem with the current NVIDIA X Server software. It's really anoying so I hope this gets fixed ASAP. 



For people that want to watch Youtube video's: it crashes a lot less when you're using the HTML5 instead of Satan spawned Flash.


NVIDIA Driver version: 295.40

Server Version #: 11.0
Server Vendor Version: 1.11.3 (11103000)
NV-CONTROL Version: 1.27
Screens: 1


Graphic Processor: GeForce 9800 GT
CUDA Cores: 112
VBIOS Version: 62.92.00.00
Memory: 1024 MB
Memory Interface: 256-bit

---

### Post by dmdelorme on 2012-05-02
I had this problem with my old laptop 11.10 and a Nvivia graphics driver i had to roll back a few versions before it was corrected. It sounds like a a bit more chronic though. is your system clean ie dust. you could have a defective graphics adaptor or bad ram. does it run hot?? what % does the Cpu run at. Is you system Bios up to date?
Run compiz with the default it can really give users issues if you set the wrong setting LOL why give us a choice if it breaks stuff but i guess that is Linux and that is why I like it :)

Sorry to though so many questions at you. 
I know squat about log files but i would start to read though them to see if there is any thing there that might shed some light on it. 
try some thing like this to get an update from dmesg
 watch 'dmesg | tail -50'
see man tail or man watch for more information

or google tail dmesg or another more appropriate log file  it could be redirected to a file and run from a terminal if the system crashes the last lines might have the errors in it. with out having to sort though the whole file to find your problem. this advice could be wrong but a little work on your part might lead to the correct answer.

---

### Post by meduser on 2012-05-04
> **dmdelorme said:**
> I had this problem with my old laptop 11.10 and a Nvivia graphics driver i had to roll back a few versions before it was corrected. It sounds like a a bit more chronic though. is your system clean ie dust. you could have a defective graphics adaptor or bad ram. does it run hot?? what % does the Cpu run at. Is you system Bios up to date?
Run compiz with the default it can really give users issues if you set the wrong setting LOL why give us a choice if it breaks stuff but i guess that is Linux and that is why I like it :)

Sorry to though so many questions at you. 
I know squat about log files but i would start to read though them to see if there is any thing there that might shed some light on it. 
try some thing like this to get an update from dmesg
 watch 'dmesg | tail -50'
see man tail or man watch for more information

or google tail dmesg or another more appropriate log file  it could be redirected to a file and run from a terminal if the system crashes the last lines might have the errors in it. with out having to sort though the whole file to find your problem. this advice could be wrong but a little work on your part might lead to the correct answer.

I have 12 gigs of ram (Mushkin Enhanced Blackline Frostbyte PC3-12800 12GB 3X4GB DDR3-1600 CL9-9-9-24 Triple Channel Memory)and my cpu is a AMD FX 4-Core Black Edition. I am not under powered, as I have over 500 watts on the power supply. My mother board is an Asus, and brand new 6 months ago. The pc is not over clocked, but I could very easy hype it up, but it is not needed. 

My video card is an geforce 9600, dual monitor with hdmi out. I don't game, so it is overkill for what I do. 

I have an Antec case with 5 fans. The cpu is never over 30degrees, and video card is never hotter than mid 70's. According to the monitors anyways. 

I don't believe this is my hardware's issues. , as all is new in the last 6 months, and windows on the dual boot is flawless...well as far as windows goes anyways.

I got impatient looking for a fix to the freeze, so I started over, and reinstalled 12.04 LTS from a clean download. It seems to have been a corrupted download of the iso, as now I am running perfectly with the fresh install.

---

### Post by sjnovick on 2012-05-06
My 12.04_AMD64 system is freezing up too!  Requires a hard reboot.

I'm running an Intel core i5 processor with 4GB RAM Intel Sandybridge mobile graphics.

Can anyone help diagnose?

Everything worked fine in 11.10.  Or, at least, no system freezes.

---

### Post by dmdelorme on 2012-05-06
Read the thread above and see if that helps... I disabled my 2 finger scrolling on my touch pad and the crashes stopped. But that could have also been just a software update.

---

### Post by user2010 on 2012-05-06
I was upgrading Ubuntu 12 and working with other programms. Suddenly everything dissapeared from display - just desktop image. The I rebooted the system manually and now I have big black terminal window and I don't know how to get usual start of ubuntu. SOS!
 
The installation wasn't finished. What could I do to fix this problem?

---

### Post by bkline on 2012-05-16
I just started having the same problems this morning.  The symptom that caught my eye was the mouse cursor behavior, which seems to have a mind of its own, very sluggish, but I can tell the system is detecting and responding to (if slowly) at least some of the mouse movement events.  No keyboard events are responded to other than the SysRq key combinations the kernel accepts.  Ctrl+Alt+Fn doesn't work.  And sshd won't accept connections when it happens.  And it's happening more and more frequently (three reboots this morning, each more closely on the heels of the previous).  Until this is fixed, my main workstation is toast.

This is Xubuntu 12.04.  Didn't happen immediately after the upgrade, which was a few days after release.

---

### Post by bkline on 2012-05-18
Other symptoms included lots of flickering pixels on a monitor that works just fine with another OS.  I believe I have solved the problem by uninstalling the nvidia proprietary drivers.  We'll see.

---

