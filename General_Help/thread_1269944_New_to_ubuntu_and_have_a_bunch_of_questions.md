---
title: "New to ubuntu and have a bunch of questions"
date: 2009-09-18
forum: General Help
---

### Post by razor180 on 2009-09-18
alright, I recently got ubuntu studio (I know they're almost exactly the same, just studio has a different theme and is geared mostly to multimedia production) and I stopped using it for a couple of weeks because it annoyed me badly (wasted 5 and a half hours on something on inkscape that ubuntu froze up on when I tried to save it, I think it's a bug in force quit, I'll explain later)

I got the 9.04 version (from what I've heard from other users, probably the reason behind some of the problems I've been experiencing, but I can't get an older version because the latest version of blender only supports 9.04) and here's some problems I've been experiencing that I'd like to get fixed (I like ubuntu, a LOT faster than vista). 

First off, I think there's a bug in force quit, because this has happened to me 3 times, all because of force quit, and nothing else seems to be causing this problem and this seems to happen everytime I use it. what's been happening is that when I use force quit, sure it quits the application, but what happens is that I can't start any new applications, then I can't properly close any later ones (or modify them in any way, which is what happened in inkscape, I had to force quit firefox, and when I tried to save something in inkscape, a modification, it froze when I clicked save) then when I try to shut down the computer, I have to hard reset because when I click on restart or shutdown (after using force quit anytime during that that session) it will freeze up and nothing will happen (I know because I waited 15 minutes on it). 

next, I need to know how to install nvidia graphics drivers onto ubuntu for my 8600GT, the xserver is running fine except it will not run my second LCD monitor, and I've heard I need to get the proper drivers, so I have them off of the nvidia site (on my desktop) and I have no idea how to run it (a .run file, nvidia had some instructions, but they were scattered and hard to follow, and I don't want to really screw things up using the terminal, so I don't want to mess with something I don't know)

next, I'm having trouble installing tar.bz or tar.bz2 and tar.gz files, I've heard different ways to install them, and so far none of them have worked

and last, I'm having trouble running chatrooms (deviant art chatrooms to be specific). on it it says javascript didn't run and flash didn't either and the fact that the javascript didn't run may have been keeping flash from running (I downloaded the extension I needed, I've gotten the firefox plugins for flash and java, and still nothing, now I've heard this has nothing to do with ubuntu, just an error in the linux version of firefox). Now I did upgrade from firefox 3.0 (provided) to firefox 3.5 (using synaptic), but this problem was happening on 3.0 and is still happening on 3.5 (which is the main reason I upgraded to 3.5, because I thought it might be fixed)

---

### Post by undecim on 2009-09-19
Most graphic drivers can be installed by going to System -> Administration -> Hardware Drivers.

If you don't see any options there, the nvidia drivers can also be installed from the ubuntu repositories. Go to your Applications menu and select "Add/Remove..." then change the "show" drop down menu to "All available applications". After that, just type "nvidia" in the search box, then select the driver that corresponds to your video card.

You may also want to install the "NVIDAI X Server  Settings" package, which will give you more control over your video card, and the "Ubuntu restricted extras" package, which will include flash player plugins, java, MS fonts, audio codecs, etc.

As for the force quit issues you have, it seems that your system is under high load? Though that doesn't seem right because if that is the same machine you've tried Vista on, it should run Ubuntu (or any other Linux distro) just fine. This could be because the CPU is working where your graphics card should be (this should be remedied by the nvidia drivers)

programs distributed as .tar.gz or .tar.bz2 files are usually (although not always) source code files. .tar.gz or .tar.bz2 files are just compressed archives (think .zip files). Usually, the programs you need will be in the ubuntu repositories (Add/Remove...). If you need to install a program that isn't in the repositories, check the program's web site first for a .deb file, which will point-and-click install in most cases (although sometimes you will need to install some dependencies).

If you need to compile a program from source. Look at [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by razor180 on 2009-09-19
okay thanks :D

now my PC being under high load isn't as unusual as you think, it was BARELY able to run vista (simple functions on vista were becoming very long and bugs were occurring due to that) because my CPU is an amd athlon 3800+ single core clocked at 2.4ghz (BIOS won't let me overclock, even if I got an aftermarket cooler, and it's very slow) and the max amount of ram allowed on the motherboard is 2gb (the ones I have in there are ddr2 667mhz) but I do have the indicator on my bar, and it's usually saying 1ghz. so my PC is slow (planning on upgrading, just not enough money yet)

well thank you for the help (and I did check the graphics drivers settings, it said I was running on the latest drivers, but I'll check with what you said)

btw, I do have a feeling xserver is going to ask me to restart xserver in order to have the updates take affect. How do I do that?

everytime I try to save the xserver settings, I get this error (and I switched to the 173 drivers, seems they were more compatible with my card than the 180 drivers, but this has done this on both) "failed to parse existing x configuration file 'etc/x11/xorg.conf'!" then when I click ok, the x server settings window closes

---

### Post by razor180 on 2009-09-19
okay, a huge error happened

I tried installing the package you suggested (and changed my graphics drivers to 173 instead of 180)  and when it was almost done installing ubuntu restricted packages, it locked up and wouldn't go, I thought it would fix itself, but I ended up going to sleep, waking up the next morning, went to the computer, and it was still locked up. so I had to hard reset the PC (again) then started up ubuntu and I got the linux shell (it loaded up ubuntu studio and instead of seeing all of the guis, the screen went black and asked me for my username then password, I gave it) then it told me x.org messed up (probably due to my change in graphics drivers). so I tried a few things (I don't know many commands, just a few) but I was able to get the system to restart, so I ran ubuntu in recovery mode, told it to fix x.org (probably just restart it, I'll explain that in a minute) then told it to fix dpkg (just in case) then told it to fix any updates (that ended just going into a loop trying to fix the fonts packages) so I got it to end (waited about half an hour before I did that) so I just ended up starting ubuntu normally, and it's fine except for a few things.

xserver's drivers are off (easy fix) but it's doing the same thing it did when I ran ubuntu for the very first time. My second screen is mirroring my first screen, and when I apply the drivers, the second screen is off and I can't get xserver to run it (I try applying the settings and I get the error message I posted above). and some other settings were changed (I only have to 2 work places, I did have 4, not a big change, but I wonder what other changes were set back to default)

EDIT: well I'm not sure how to put most of the graphics processing on my GPU, but I have gotten my second screen to work (and it's fine, no problems). I'm using the 180 nvidia drivers and not the 173 (which I thought using 173 would fix the problem, but it just wouldn't work). I'm still having the other problems, but that one is fixed (just need to get the deviant art chatroom working again)

---

### Post by razor180 on 2009-09-21
okay, new problem, while my computer was rendering at home (I was away from home) my power shutdown (power surge caused by a thunderstorm), now there are 2 problems
1. I think the rendering process may have been done because the storm started just a couple of hours ago, so I need to know where blender would store images (I didn't save it, but I'm sure it's in a render buffer of some sort) because with my slow computer, it'll take another 15 hours or so to render
2. This unexpected shutdown seems to have damaged my drivers, I turned the computer on after coming home, and got an error message saying my x.org drivers weren't working properly (and I'm using the 180 version drivers, I got the same message with the 173 drivers, didn't get it on the 180 drivers, and now I am). so I went to recovery mode, had it reset my graphics, then logged in, used the 180 drivers again, restart, then the same error message came up.

maybe I should just completely get rid of the drivers off of my PC then put them back in (may be a bad spot on the hard disc due to the power surge and my hard reseting, which I had to do due to errors in ubuntu, ones that completely froze my PC... often)

EDIT: okay, the drivers are working, I just have one problem I can't get it to save the x config file, and I tried manually removing the backup that's keeping it from saving (not sure why it's doing that though) but it won't let me, so I'm stuck there

I'm also having no luck thus far on finding the buffered image of my render

I'm going to try that, and I'll tell you if that works

---

### Post by razor180 on 2009-09-23
I'm bumping this because I really need this fixed and the only ones that seem to get replies on are on the top of the list and the list changes fast

my problems are:

I can't save the X.org configuration because it keeps on telling me that x.conf.backup can't be replaced, and I don't know how to fix that

---

### Post by bonnerb on 2009-09-23
When I try to do anything, I'm asked for my admin password. I wrote down but it does not work.
I'm totally frustrated with this.
Also, when I go to terminal and type sudo (anything) it asks for a password but the keyboard will not put any letters or anything at the cursor. What the #$@#^

---

### Post by bonnerb on 2009-09-23
I can not get any where with this OS.

---

### Post by razor180 on 2009-09-24
> **bonnerb said:**
> When I try to do anything, I'm asked for my admin password. I wrote down but it does not work.
I'm totally frustrated with this.
Also, when I go to terminal and type sudo (anything) it asks for a password but the keyboard will not put any letters or anything at the cursor. What the #$@#^
first off, make sure the password is correct

and in the terminal, since it can't mask passwords, it just leaves a blank, letters are there, they're just not visible

second, next time, please make your own topic (unless it pertains to a problem of the topic maker)

---

### Post by kimo9909 on 2009-09-24
> **razor180 said:**
> I'm bumping this because I really need this fixed and the only ones that seem to get replies on are on the top of the list and the list changes fast

my problems are:

I can't save the X.org configuration because it keeps on telling me that x.conf.backup can't be replaced, and I don't know how to fix that

Try this as is should give the NVidia Display Manager write permissions.

1) Press Alt + F2 and then type 'gksu nvidia-settings' to bring up the NVidia X Server Settings dialog.
2) Choose 'X Server Display Configuration
3)  Make the changes and then save the configuration.

---

### Post by zinouch on 2009-09-24
i've a vaio nr21z, with a Nvidia 8400 GT, i use the "add/remove application" and i find "nvidia" after that i select the "Nvidia X server seting" and a restar my computer when this last is downloaded and instaled.
next, a go to "system>hardward drivers", i select the last drivers of my nvidia, they can be 177 or 186 or something else ...and i puch "install", now a restard my computer and i go in the next to "system > nvidia X server seting" here you can adjust the constat, color ... everything.

you should maybe use "gksu nvidia-settings" with ALT+F2 or maybe in TERMINAL :lolflag:

have a good day

---

### Post by razor180 on 2009-09-25
> **kimo9909 said:**
> Try this as is should give the NVidia Display Manager write permissions.

1) Press Alt + F2 and then type 'gksu nvidia-settings' to bring up the NVidia X Server Settings dialog.
2) Choose 'X Server Display Configuration
3)  Make the changes and then save the configuration.
okay, I did say it didn't work because I couldn't get alt f2 to work, but it worked, thanks

---

### Post by razor180 on 2009-09-25
> **zinouch said:**
> i've a vaio nr21z, with a Nvidia 8400 GT, i use the "add/remove application" and i find "nvidia" after that i select the "Nvidia X server seting" and a restar my computer when this last is downloaded and instaled.
next, a go to "system>hardward drivers", i select the last drivers of my nvidia, they can be 177 or 186 or something else ...and i puch "install", now a restard my computer and i go in the next to "system > nvidia X server seting" here you can adjust the constat, color ... everything.

you should maybe use "gksu nvidia-settings" with ALT+F2 or maybe in TERMINAL :lolflag:

have a good dayokay, wrong problem, my problem is that it will not write the configuration file because for some reason it can't rewrite the configuration backup (which for some reason in the programming, it has to be able to rewrite that in order to work) file, plus, I have the nvidia x server settings installed already, so I believe you've stated the wrong problem

and it won't matter if it's in terminal or if it's in gui, the only thing starting it in terminal allows you to do is use the terminal for that particular program, not give it special permissions

---

