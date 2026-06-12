---
title: "How to configure my capture card"
date: 2010-05-04
forum: General Help
---

### Post by TurboThiago on 2010-05-04
Hi guys,

I have a capture tv card in my pc, but i can't configure it. It's a TV Tuner PRO ENLTV-FM  Encore Electronics.  I have all the System Requeriments and I've downloaded a program called MeTv to use it, but it's not working. The message that i have of this program is: 
```
There are no DVB Tuner Devices
``` 
I've read on the net that I have to alter something in the kernel called bttv with the values: card and tuner. So I think the command is:

```
chmod bttv card=# tuner#
```

where "#" is the value of my tv card and the tuner, but i don't know if this command is correct and which value to put. Does someone know what to do? 
Thanks

PS: I use ubuntu 9.10 64bits

---

### Post by inameiname on 2010-05-04
I'm not sure what all that you mentioned does, but this is how I installed mine (actually two, one USB analog/digital and one PCI capture card), which I think is a basic way to do so.

First I installed the firmware of my drive, which wasn't already in the firmware folder, and then went to this site ([http://linuxtv.org/repo/](http://linuxtv.org/repo/)) and downloaded and installed the two tar files (which means extract and open a terminal in that folder, and 'make' and 'sudo make install'): 

V4L-DVB and DVB-APPS

However, I noticed with Lucid, you have to do one more thing:
In the 'v4l' folder, open the .config file in the 'v4l' subfolder (created only after you 'make' it first), and find the line: CONFIG_DVB_FIREDTV=m and change it to CONFIG_DVB_FIREDTV=n, and then 'make' (again) and 'sudo make install'. (FYI, this all takes several minutes.) Then reboot.

There is also a repo for V4L, which will keep you up-to-date:
deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) lucid main

Again, this is how I use it, and I don't use MeTv, which seemed too complicated for me to just watch tv. Hehe. I use Tvtime for analog cable (latest working deb found here: [http://packages.debian.org/search?searchon=names&suite=all&section=all&keywords=tvtime](http://packages.debian.org/search?searchon=names&suite=all&section=all&keywords=tvtime)) and SMPlayer for digital.

---

### Post by dino99 on 2010-05-04
first you need to check if your hardware is found: system - admin - hardware driver

is the prog you have installed is designed for linux ?

google around: your hardware+linux or ubuntu

---

### Post by TurboThiago on 2010-05-05
Hi guys,

I'm trying to configure it. But i've stopped for a while because i was configuring php. But now i'm back.

> first you need to check if your hardware is found: system - admin - hardware driver

is the prog you have installed is designed for linux ?

google around: your hardware+linux or ubuntu 

Dino99, I've looked in system-admin- hardware driver and it says that all the drivers are installed. I think it can be solved by this way. I've serached on the net and I think my product is designed for windows, but it can be used in linux too, but i'm not right of it. My teacher have installed a card, so I think i can do it too. 

> I'm not sure what all that you mentioned does, but this is how I installed mine (actually two, one USB analog/digital and one PCI capture card), which I think is a basic way to do so.

First I installed the firmware of my drive, which wasn't already in the firmware folder, and then went to this site ([http://linuxtv.org/repo/](http://linuxtv.org/repo/)) and downloaded and installed the two tar files (which means extract and open a terminal in that folder, and 'make' and 'sudo make install'): 


My card is a pci one. I've been in this site, but i don't know what file to download; there is a lot. :-k 
And it says something about watch from my browser. I don't want it. I just want to watch my tv cannels and convert my old vhs to dvd, that I used to do in windows. 
Is this the drivers to the card? Or, is it just to watch in browser? i'm confused.

Thanks

Thiago

---

### Post by inameiname on 2010-05-06
Basically to get them working, you need the firmware for it (for me my USB one required me to manually throw it into the firmware folder, which I found online, and the PCI capture card required none, as it must've been more a plug and play one because I didn't need anything else) (perhaps like yours), AND then you need those two things I mentioned: V4L-DVB and DVB-APPS.

Click to download the V4L-DVB one: [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
Click to download the DVB-APPS one: [http://linuxtv.org/hg/dvb-apps/archive/tip.tar.bz2](http://linuxtv.org/hg/dvb-apps/archive/tip.tar.bz2)
...and then just extract, open a terminal into that folder that you just made, and then follow the above instructions I mentioned.

How that helps. It took me a while myself to figure out how to install and use my cards too, so I know it can suck figuring it all out.

Oh, and that thing about opening a browser was merely a how to instruction on how to open those two links I gave you and open them through your browser, that's all. You can just ignore all that, as my instructions are pretty much the same.

One thing to note, I personally haven't figured out entirely how to easily record, just play. Though, there are terminal ways, and perhaps you can get MeTV to work for that, IDK. Regardless, my instructions are just to get the drivers, which you need to record and/or play. So I'd say first see if you can play, and then next see how to record.

---

### Post by TurboThiago on 2010-05-07
OK, I'll try to download these files and cofigure them. 
Thanks. If I have some problem I'll tell you.

bye

---

### Post by TurboThiago on 2010-05-12
Hi, My time is so short, because there is a lot of things to do :P, but today I've tried to do it, but i've found some problems. I did not find that .config file. But there is a lot of "confs" there:
config.bttv
config.cx88
config.saa7134
config-compat.h
Kconfig
Kconfig.kern
sn9c102_config.h
Kconfig.sound
Kconfig.staging
I think it's all. Is this ".config" one of those "configs" file that i've found? I've opened config-compat.h, and i've found a CONFIG_DVB_FIREDTV, but it's not receiving any value like n or m that. It is like this: 

```
#undef CONFIG_DVB_FIREDTV
#undef CONFIG_DVB_FIREDTV_MODULE
#define CONFIG_DVB_FIREDTV_MODULE 1
```

What should i do?

Thanks

---

### Post by inameiname on 2010-05-12
Just as with any file or folder that is hidden in Nautilus, you must have "Show hidden files" checked under "View" in the Nautilus menu to be able to see any file or folder with a '.' before it. Should've mentioned that.

---

### Post by TurboThiago on 2010-05-15
hi everybody,

inameiname, even showing the hidden files, i did not find the .config file. I think it is not there. And i don't know if i have done something wrong. What can be?

Thanks 

Thiago

---

### Post by inameiname on 2010-05-15
Alright, uhm, I'm not sure what's going on for you. But here's my steps for that V4L-DVB file that you need:

Click to download the V4L-DVB one: [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

I save it in a 'Temp' folder. Go into that folder, and find the '.bz2' file. I right click it, and there is an option to extract here. Then a folder is made of the same name. I right click on that folder, and 'open-in-terminal' (if you have that nautilus extention, otherwise open using a script or through the terminal). Then in the terminal, type 'make', and wait a minute or two. And once that's done, go into the very same folder, (and make sure you have 'Show hidden files' checked), and in the 'v4l' folder, you'll find a .config file. Open it, and change the line: CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n, and then go back into the terminal, and type  'make' (again) and when that's done, 'sudo make install'. (FYI, this all takes several  minutes.) Then reboot. 

And also make sure to also 'make' and 'sudo make install' the dvb-apps tar file as well using the same manner, minus the extra '.config' thing you have to do.

As far as why you aren't seeing the '.config' file, maybe there is something wrong with your 'make' and 'sudo make install' programs and installation. Here are the things I add which from research help or are required for that process: might as well just install these, as they are not very large (I added the nautilus-open-terminal because it's handy):

sudo apt-get install build-essential make automake nautilus-open-terminal

---

### Post by izh34 on 2010-05-29
> **inameiname said:**
> Alright, uhm, I'm not sure what's going on for you. But here's my steps for that V4L-DVB file that you need:

Click to download the V4L-DVB one: [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

I save it in a 'Temp' folder. Go into that folder, and find the '.bz2' file. I right click it, and there is an option to extract here. Then a folder is made of the same name. I right click on that folder, and 'open-in-terminal' (if you have that nautilus extention, otherwise open using a script or through the terminal). Then in the terminal, type 'make', and wait a minute or two. And once that's done, go into the very same folder, (and make sure you have 'Show hidden files' checked), and in the 'v4l' folder, you'll find a .config file. Open it, and change the line: CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n, and then go back into the terminal, and type  'make' (again) and when that's done, 'sudo make install'. (FYI, this all takes several  minutes.) Then reboot. 

And also make sure to also 'make' and 'sudo make install' the dvb-apps tar file as well using the same manner, minus the extra '.config' thing you have to do.

As far as why you aren't seeing the '.config' file, maybe there is something wrong with your 'make' and 'sudo make install' programs and installation. Here are the things I add which from research help or are required for that process: might as well just install these, as they are not very large (I added the nautilus-open-terminal because it's handy):

sudo apt-get install build-essential make automake nautilus-open-terminal

I still don't get it. I had tried all the method you give there but my tvtime won't show anything. Just a blank screen. No button for scanning. Is this mean it stillcan't detect my tv card?

---

### Post by inameiname on 2010-05-30
Perhaps you just need to quickly tweak tvtime. Some of these can be done within tvtime itself. Just right click anywhere in the tvtime screen.

To change the default video input setting if you have to, which you may or may not:

(For me, my webcam is (video0), not my tv tuner, which is (video1)):

        tvtime-configure -d /dev/video1 (or leave at default /dev/video0 if need be)

    Other configurations:

        tvtime-configure -h        

To scan for analog channels:

    tvtime-scanner

So basically go to the terminal and use

tvtime-scanner, and see what happens. Obviously, you must have your card hooked up to the cable and all that beforehand, so it can scan. In the end, you should get an .xml file in the .tvtime folder which will list all of your analog cable stations.

UPDATE:

Oh, and I almost forgot, the tvtime that is in the lucid repos doesn't  seem to work correctly. At least for me. So if you experience the same  issues, what I did is just installed a later version from the debian  repository, [http://packages.debian.org/sid/tvtime](http://packages.debian.org/sid/tvtime) (links are on the bottom), and it works just  fine.

---

