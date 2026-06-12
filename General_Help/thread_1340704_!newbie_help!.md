---
title: "!newbie help!"
date: 2009-11-28
forum: General Help
---

### Post by Isaacgallegos on 2009-11-28
I have a hauppauge 1250 wintv card. 
My tv playing software wont use it because I need a driver:
**v4l-dvb**
but I can't seem to just load it using the synaptic package manager.

Is there some easy way of loading it I'm missing? 

I'm pretty new to linux.

Please give me some assistance instead of making me bump a million times with no solution.

---

### Post by Isaacgallegos on 2009-11-28
Ok then... time to boost my bean count...

BUMP

---

### Post by Isaacgallegos on 2009-11-29
I really hate doing this..
bump

---

### Post by NoaHall on 2009-11-29
Hm. Have you tried looking in "System -> Admin -> Hardware drivers" ?

---

### Post by Virtual Liberty on 2009-11-29
[Download]("http://www.linuxtv.org/downloads/") it and follow the instructions ( INSTALL file ) on how to compile it. As there are no pre-compiled binaries available, I doubt you'll find an easier way.

---

### Post by Isaacgallegos on 2009-11-29
excellent. But where are the instructions? And which file do I download? There are many in that directory.

---

### Post by Virtual Liberty on 2009-11-29
I think you should be fine with the [1.1.1]("http://www.linuxtv.org/downloads/linuxtv-dvb-1.0.1.tar.gz") version. Instructions are in the INSTALL file.

---

### Post by Isaacgallegos on 2009-11-29
Ah! thank you. Now I feel like I'm on the right track.

---

### Post by Isaacgallegos on 2009-11-29
Sorry. These instructions aren't written very clear. 

I went to the directory like the instructions said and typed "sudo make". Nothing really happened. 
```
eva@eva-desktop:~/linuxtv-dvb-1.0.1$ sudo make
cat: CVS/Root: No such file or directory
(cd driver; make)
make[1]: Entering directory `/home/eva/linuxtv-dvb-1.0.1/driver'
Makefile:102: /lib/modules/2.6.31-15-generic/build/Rules.make: No such file or directory
make[1]: *** No rule to make target `/lib/modules/2.6.31-15-generic/build/Rules.make'.  Stop.
make[1]: Leaving directory `/home/eva/linuxtv-dvb-1.0.1/driver'
make: *** [dvb] Error 2
eva@eva-desktop:~/linuxtv-dvb-1.0.1$ 
```

I also tried typing "make install"
```
$ make install
cat: CVS/Root: No such file or directory
make: *** No rule to make target `install'.  Stop.
eva@eva-desktop:~/linuxtv-dvb-1.0.1$ sudo make install
cat: CVS/Root: No such file or directory
make: *** No rule to make target `install'.  Stop.
eva@eva-desktop:~/linuxtv-dvb-1.0.1$ 
```



Could someone read this and tell me what I need to do? It makes no sense to me. I'm only doing the parts of this that do make sense and so far nothing has happened. 

```

Configuration:

- You must have the kernel sources for the kernel you are actually using
  installed, and symlinked to /lib/modules/$(KERNEL_VERSION)/build.
  Otherwise, change the path for KERNEL_LOCATION in DVB/driver/Makefile.

- Make sure that your kernel has enabled: 

    Video4Linux Support (CONFIG_VIDEO_DEV)
      needed by cards with integrated MPEG decoder to display video on screen
 
    Input Core Support (CONFIG_INPUT)
    Event Device Support (CONFIG_INPUT_EVDEV)
      needed by the DVB remote control driver

- Login as root, change to the directory DVB and type "make".
  This will build the drivers and all utility and test programs.

- If everything compiled without errors, cd to DVB/drivers and
  type "make insmod" to load the modules. Depending on your hardware
  you may append a "CARDS=av7110" or "CARDS=b2c2" to the "make insmod"
  command line to avoid loading unnecessary drivers (optional).
  During the installation of the modules your PC can "hang" for a
  few seconds. This happens during the loading of the ARM application
  ("firmware") into the DRAM of the AV7110 and is "normal".

  If the drivers work you can install them permanently using "make install".
  See drivers/modules.conf for some hints how to enable autoloading.

- If you don't use devfs, execute DVB/driver/makedev.napi to create
  the device nodes; if you use devfsd, copy drivers/devfsd.conf to
  /etc/devfs/conf.d/dvb (exeact location might depend on you distribution).

- apps/szap/ contains three simple applications for zapping with
  DVB-S, DVB-C or DVB-T cards (szap/czap/tzap); read the comments in
  apps/szap/szap.c for instructions.
  Note 1: tuning succeeded if you see the FE_HAS_LOCK flag and "status 1f";
  	  a good signal has a low bit error rate (ber) and zero
	  uncorrectable packets (unc).
  Note 2: you must keep ?zap running, or the frontend will go to sleep
          (unless you load dvb-core.o with dvb_shutdown_timeout=0)

- If your card has a hardware MPEG decoder you can watch TV
  with xawtv (together with e.g. szap for DVB tuning);
  Note: xawtv cannot control the DVB tuner, you must use ?zap

- For cards without hardware MPEG decoder you need a software
  MPEG decoder, e.g. mplayer or xine (you need *very* recent versions
  which understand MPEG2 transport streams; xine v0.9.21 and
  mplayer dev-CVS-030723-16:39-3.3.1 seem to work);
  Note: You must run ?zap with the -r flag to enable stream output to
        the dvr device, and keep it running while watching tv.
  Examples:
    mplayer - < /dev/dvb/adapter0/dvr0
    xine stdin://mpeg2 < /dev/dvb/adapter0/dvr0
  Note: Newest mplayer and xine versions are reported to have
  builtin DVB support (see FAQ for more info).

```

---

### Post by Isaacgallegos on 2009-11-29
bump

---

### Post by Isaacgallegos on 2009-11-29
bump

---

### Post by Isaacgallegos on 2009-11-29
bump!

---

### Post by wcutrombonekid on 2009-11-29
i am no help
i realize this must be frustrating, what with all the bumping

it helps if you put a more descriptive title on your thread.  there are a lot of "newb help"s and "help me please"s out there

the more descriptive title will draw the people you need that can help you fix it

i would make a new title and you will probably get it solved a lot faster

---

### Post by cariboo on 2009-11-29
Please don't bump more than once every 24 hours. Remember we are all volunteers here, and the person that can answer your question may not have seen this thread yet.

---

### Post by running_rabbit07 on 2009-11-29
> **cariboo907 said:**
> Please don't bump more than once every 24 hours. Remember we are all volunteers here, and the person that can answer your question may not have seen this thread yet.

Not to mention that most people who can help sometimes don't click on threads with multiple responses, because they may think you are already being helped.

---

### Post by Isaacgallegos on 2009-11-29
Did you read any of the issues I had? I'm not asking people to solve a problem. I'm trying to just compile something for the first time.

---

### Post by Isaacgallegos on 2009-11-29
> **cariboo907 said:**
> Please don't bump more than once every 24 hours. Remember we are all volunteers here, and the person that can answer your question may not have seen this thread yet.
If you compiled something before read my post and tell me what I need to do to compile this thing. Is the process so different I need the right person to come by and tell me what to do? Cant any of you normal linux users just let me in on the secret?

---

### Post by oldos2er on 2009-11-29
V4l is already in the kernel, so I don't think you need to compile and install anything. Can you please post the output of **lspci** run in a terminal?

---

### Post by Isaacgallegos on 2009-11-29
It is? All that time spent on trying to get it on! 
> 00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:03.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port B)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
The card is:
Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)

Thanks for giving me your time!!!!

---

### Post by oldos2er on 2009-11-29
You can install a program like xawtv or tvtime just to double-check that it works.

---

### Post by Isaacgallegos on 2009-11-29
I tried those and a others. Including mythtv. none work. 

tvtime says it can't open the card.

---

### Post by Isaacgallegos on 2009-11-29
But i read that it's because my chip set needs those drivers.

---

### Post by Slim Odds on 2009-11-29
> **Isaacgallegos said:**
> I really hate doing this..
bump

We hate it even more than you do......

Knock it off!!

---

### Post by teward on 2009-11-29
Have you tried updating your chipset?  That would be my first recommendation.

And about the bumps, I agree with Slim Odds.  **Stop the bumping, or NOBODY will help you**.

---

### Post by Isaacgallegos on 2009-11-29
> **Slim Odds said:**
> We hate it even more than you do......

Knock it off!!
Why? no one would ever read this then. Oh and try reading my whole post. 

> **TrekCaptainUSA said:**
> Have you tried updating your chipset?  That would be my first recommendation.

And about the bumps, I agree with Slim Odds.  **Stop the bumping, or NOBODY will help you**.

Ok I googled it. Now what? 

[http://www.google.com/search?source=ig&hl=en&rlz=&q=ubuntu+update+chipset&aq=f&oq=&aqi=](http://www.google.com/search?source=ig&hl=en&rlz=&q=ubuntu+update+chipset&aq=f&oq=&aqi=)

And I'll only bump this once it needs to be again. People will never see this. I have no other choice.

---

### Post by jimko on 2009-11-29
Having a similar problem with my 1250 card since a fresh Karmic install. (worked ok after a jaunty-to-karmic update, but then failed after the fresh install) I don't think it's my v4l drivers in general, because a different card works fine (kworld 110).

The 1250 card isn't supposed to need firmware, but I'm getting firmware related errors in my dmesg

```
$ dmesg | grep -i Haup
[   11.816903] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   11.944580] tveeprom 1-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   11.944583] cx23885[0]: warning: unknown hauppauge model #0
[   11.944585] cx23885[0]: hauppauge eeprom: model=0
```

---

### Post by running_rabbit07 on 2009-11-29
[http://www.amazon.com/Hauppauge-1196-HVR-1250-Express-Definition/product-reviews/B0014YFC18/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1](http://www.amazon.com/Hauppauge-1196-HVR-1250-Express-Definition/product-reviews/B0014YFC18/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1)

---

### Post by Grunmooz on 2009-11-29
:popcorn:

---

### Post by Isaacgallegos on 2009-11-29
> **jimko said:**
> Having a similar problem with my 1250 card since a fresh Karmic install. (worked ok after a jaunty-to-karmic update, but then failed after the fresh install) I don't think it's my v4l drivers in general, because a different card works fine (kworld 110).

The 1250 card isn't supposed to need firmware, but I'm getting firmware related errors in my dmesg

```
$ dmesg | grep -i Haup
[   11.816903] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected]
[   11.944580] tveeprom 1-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   11.944583] cx23885[0]: warning: unknown hauppauge model #0
[   11.944585] cx23885[0]: hauppauge eeprom: model=0
```

I have the exact same readout. Exactly! Please keep in touch! I feel a solution is near.

---

### Post by Slim Odds on 2009-11-29
> **Isaacgallegos said:**
> Why? no one would ever read this then. Oh and try reading my whole post. 

I read lots of posts and help lots of people and you are one of the most annoying I've seen here.

As was mentioned to you, we come here on our own time to help out. We don't need anyone demanding attention (bump, bump, bump....) as if we owe you something.

So you might want to consider being a little more considerate of this great FREE resource.

---

### Post by Isaacgallegos on 2009-11-29
> **Slim Odds said:**
> I read lots of posts and help lots of people and you are one of the most annoying I've seen here.

As was mentioned to you, we come here on our own time to help out. We don't need anyone demanding attention (bump, bump, bump....) as if we owe you something.

So you might want to consider being a little more considerate of this great FREE resource.

You're confused as to why I'm bumping and unsure of what is considered a lot of bumping... I'm glad you read posts but it seems that your contribution here has little to do with any solution.

---

### Post by Isaacgallegos on 2009-11-29
double post.. oops..

---

### Post by Slim Odds on 2009-11-29
> **Isaacgallegos said:**
> You're confused as to why I'm bumping and unsure of what is considered a lot of bumping... ...

LOL, I'm confused?

A) I don't care why you're bumping 3 times an hour.
B) YOU are the one who needs to stop bumping 3 times an hour.

Hereafter, I will ignore all of your posts.
Good luck with anyone else here giving you help.

---

### Post by running_rabbit07 on 2009-11-29
> **Slim Odds said:**
> LOL, I'm confused?

A) I don't care why you're bumping 3 times an hour.
B) YOU are the one who needs to stop bumping 3 times an hour.

Hereafter, I will ignore all of your posts.
Good luck with anyone else here giving you help.

The funny part is that the OP could have Googled for a compile HowTo and had his driver installed by now.

**OP, Go to the bottom of [this page]("http://www.psychocats.net/ubuntu/installingsoftware") where it teaches how to compile programs and drivers.**

Google is your friend.

---

### Post by jimko on 2009-11-29
I have successfully recompiled the v4l-dvb drivers and it has not helped. I'm giving up for tonight, but I'll keep working on this issue. Just for the record, here's the process to compile the drivers on karmic:

```

#Get the stuff you need to be able to compile
sudo apt-get install build-essential mercurial linux-headers-`uname -r`
cd /usr/src

#Get the driver source code
sudo hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb

# If you compile now, there will be an error. Edit the .config file
# change CONFIG_DVB_FIREDTV=m
# to CONFIG_DVB_FIREDTV=n
sudo gedit ./v4l/.config

sudo make
sudo make install
# Reboot

```[Link to the compile process]("http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10")
[Link to the correction needed in the config]("http://ubuntuforums.org/showthread.php?p=8333223")

My lspci output looks like the original poster's. Here's the 2 vid cards. 
```
$ lspci | grep -i -e cx -e saa
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)
$
```I have a /dev/dvb/adapter[0,1] and they both have contents, but I only have a /dev/video0 which is the Kworld saa7133 card.

lsmod reports the cx2388 module is loaded. My gut feel is it's that module or something it depends on. 

BTW, I'm running the Mythbuntu karmic distro and this card has been rock-solid since at least 8.04 or 8.10 when I first started with Mythtv. Never had to futz with drivers or firmware or recompile anything.

---

### Post by fluffman86 on 2009-11-29
> **Isaacgallegos said:**
> double post.. oops..

hahaha...you "double posted" 9 minutes apart, and your post saying you double posted wasn't edited.  you fail.

edit: also, you're now on my ignore list.

---

### Post by Isaacgallegos on 2009-11-30
> **running_rabbit07 said:**
> The funny part is that the OP could have Googled for a compile HowTo and had his driver installed by now.

**OP, Go to the bottom of [this page]("http://www.psychocats.net/ubuntu/installingsoftware") where it teaches how to compile programs and drivers.**

Google is your friend.

Thank you!

---

### Post by Isaacgallegos on 2009-11-30
> **jimko said:**
> I have successfully recompiled the v4l-dvb drivers and it has not helped. I'm giving up for tonight, but I'll keep working on this issue. Just for the record, here's the process to compile the drivers on karmic:

```

#Get the stuff you need to be able to compile
sudo apt-get install build-essential mercurial linux-headers-`uname -r`
cd /usr/src

#Get the driver source code
sudo hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb

# If you compile now, there will be an error. Edit the .config file
# change CONFIG_DVB_FIREDTV=m
# to CONFIG_DVB_FIREDTV=n
sudo gedit ./v4l/.config

sudo make
sudo make install
# Reboot

```[Link to the compile process]("http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10")
[Link to the correction needed in the config]("http://ubuntuforums.org/showthread.php?p=8333223")

My lspci output looks like the original poster's. Here's the 2 vid cards. 
```
$ lspci | grep -i -e cx -e saa
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 03)
$
```I have a /dev/dvb/adapter[0,1] and they both have contents, but I only have a /dev/video0 which is the Kworld saa7133 card.

lsmod reports the cx2388 module is loaded. My gut feel is it's that module or something it depends on. 

BTW, I'm running the Mythbuntu karmic distro and this card has been rock-solid since at least 8.04 or 8.10 when I first started with Mythtv. Never had to futz with drivers or firmware or recompile anything.

I'll give it a shot sometime tomorrow. Thanks!

---

### Post by Isaacgallegos on 2009-11-30
> **Slim Odds said:**
> 
Hereafter, I will ignore all of your posts.


Agreed. That would  be an improvement.

---

### Post by wcutrombonekid on 2009-11-30
reading this thread has made me want to strangle puppies

and not just the ugly ones

the cute ones too

---

### Post by Isaacgallegos on 2009-11-30
indeed.

---

### Post by lisati on 2009-11-30
> **Isaacgallegos said:**
> Why? no one would ever read this then. Oh and try reading my whole post. 


> **Isaacgallegos said:**
> You're confused as to why I'm bumping and unsure of what is considered a lot of bumping... I'm glad you read posts but it seems that your contribution here has little to do with any solution.

Some of us go looking for questions with no replies in the hope that we might find one that we can answer. If you "bump" your questions too soon, they won't show up in the search results as having "no" replies. Result: we won't see the question.

I repeat what someone else has said: perhaps the person who is able to answer your question to your satisfaction hasn't seen it yet.

p.s. My only experience of DVB-T stuff is with a set-top box. Good luck finding an answer that you can use.

---

### Post by Isaacgallegos on 2009-11-30
Thanks.

---

### Post by Isaacgallegos on 2009-12-01
Yeah. No luck on my end. I'm going to start again using mythbuntu and see if it will work on that.

---

