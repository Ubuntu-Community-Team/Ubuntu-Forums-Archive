---
title: "Intel 82865G Integrated Graphics - Need Help Installing + Finding Driver [pre-noob!!]"
date: 2009-08-14
forum: General Help
---

### Post by ipodsmakezombies on 2009-08-14
Warning!! I'm a noob! I know nothing!

[[Need help Finding + Installing Graphics Driver for Intel 82865G Integrated Graphics Controller (rev 02)]]

So I got this computer out of the goodness of my old boss' heart, she doesnt know anything about it and neither do it. It's a compaq pc with an intel graphics card and I'm convinced that it's been changed because they hired a computer expert for the company to buy the computers for them and the person cover the model number and junk on the model and im sure it's been changed somehow. Either way I can't read it and I don't really know how to find out what model I have but its a few years old with a compact PC tower design. Hope that helps. **Maybe someone can show me a way to find out what model of PC i have?**

Anyway, I've read a bunch of noob posts but I only get more confused all this terminal stuff and modprobe and they keep saying type in the driver name (what IS the name of the driver how do I find that name? what does it look like? [http://ubuntuforums.org/showpost.php?p=3306230&postcount=3](http://ubuntuforums.org/showpost.php?p=3306230&postcount=3)<----this is what I was looking at (SO CONFUSED!)

I'm not a quitter so I'm gonna get this baby running smoothly and one I think I can do that is by soaking up as much information as possible. So I'm gonna try to help you help me by giving you as much information as possible so here it goes.

***
When I look at the System Monitor it tell me in Hardward that I have
MEM: 489.6 MiB
PROCESSOR:INTEL PENTIUM 4 CPU 2.80GHz


next post has lcpi and lsmod so this one post doesnt overwhelm ppl look down
***

yea yea its an oldie and but I want to learn linux on her before I fork out the big bucks right? :P right!

I dont even know if this helps. I dont know how to find any other information other than that.

Thanks guys in advance. I also looked at this post [http://ubuntuforums.org/showpost.php?p=7104256&postcount=1](http://ubuntuforums.org/showpost.php?p=7104256&postcount=1) But I got stuck at the first one where he says "Find the "Device" section and make sure it looks identical to the following" because it doesnt look like that..does he mean just type all that in? or it should already be in there? I'm so scared to mess this thing up! plus he said noobs like me shouldn't even be following his tutorial so I'm confused there and when I tried his wget hyperlink for the file he wanted to make executable it gave me an error and suggested I try to use the help option in wget but i typed it right i thought i dunno. 

Am I just being a lil scaredy cat? should I just get in there and get my hand dirty? ubuntu is so pretty though! even without a working graphics card :P anyway, am I following the right tutorial? because it seems geared towards the new computers anyway, so im a little wary about that too.

sigh...i should end this post now before I really start talking.

thanks guys. I'm not giving up!

---

### Post by ipodsmakezombies on 2009-08-14
lscpi shows :
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
=========================

lsmod shows:
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            99648  1 
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_intel8x0           37532  4 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                61972  0 
ppdev                  15620  0 
snd                    62756  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
pcspkr                 10496  0 
serio_raw              13444  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
shpchp                 40212  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
intel_agp              34108  1 
agpgart                42696  2 intel_agp
usbhid                 42336  0 
tg3                   131204  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
============================

***
I dunno if any of this helps. my xorg.conf or whateever file in completely emtpy and my driver thing is emtpy too the manager thing.. you know what im talking about right? I went to intel.com for the linux driver for my specific model of integrated graphics controller and downloaded the driver it was unzipped and i dont know what to do with it...i clicked the "install.sh" file did nothing. RUN in Terminal..nothing. Reboot..nothing. RUN .. nothing...i duno what i'm supposed to be doing with it...what IS the driver?! lol so confused right now

---

### Post by john stiles on 2009-08-14
I'm a bit confused. You seem to be reading info from the screen, so I'm unclear what the problem is. It does not sound as if you need to add anything. All the "drivers" for older models/hardware are built into the kernel and would have been installed by default.

A simple test would be to burn a live Cd and see if the machine boots from that and operates, but it sounds as if you are way past that point.

---

### Post by michy99 on 2009-08-14
The drivers for most Intel graphic cards are built into the kernal. Are you having problems with your graphics?

---

### Post by ipodsmakezombies on 2009-08-14
Lol that's a good question. I think i am. I mean. I can't use SecondLife. they have a linux version and its not working will load but the only thing that wont is the graphics part. I was able to use it when I had windows XP in this so i figure i need a driver. also, simple hints like when I try to put in the visualizer in the rythmebox just crashes rythmebox that's a graphics thing right? and when i try to bump up te appearance the next mark it says it cant but doesnt tell me why. i figured its a driver. shoot could i be wrong?

---

### Post by soapBAR2 on 2009-08-14
Ok, well, firstly, that document you linked is for manually loading kernel extensions, instead of installing drivers. It's more or less the same thing from the computer's point of view, but from your point of view, it's much, much easier and safer to install drivers rather than load them into the kernel using modprobe/lsmod. Sorry, but this guy threw you in right at the deep end.

Secondly, you don't install things on linux the same way you install things on Windows. On windows, you download the installer from your web browser and run it. On linux, you either use the package manager (best option), or compile it yourself (hardest option). The package manager on Debian-based distributions (including the Ubuntu sub-family) is the .deb/apt (you have 2 programs by default for installing from repository - apt-get and aptitude). There are also bash scripts (which is what you've downloaded), but they're not overly common (they're mainly for proprietary software - the driver writer can't be bothered maintaining a version for every distribution, and won't hand out the source to compile).

Your xorg.conf can't be empty (like, completely devoid of text). I suspect you opened xorg without proper privileges. Just

```
sudo nano /etc/X11/xorg.conf
```

(sudo is "substitute user do" - the substitute user is root. Put it in front of any command, type your password, and you're in god-mode, which is both powerful and dangerous)

If you don't have a hardware icon in your system tray on boot (I assume you made it all the way into the desktop), and the graphics seem a bit dodgy (flickery, slow, whatever), install envyng to help you install your drivers.

GNOME/XFCE (Ubuntu, Xubuntu)
```
sudo apt-get install envyng-core envyng-gtk
```

KDE
```
sudo apt-get install envyng-core envyng-qt
```

Then, open envyng (it should prompt for password) and install the drivers from there (it's pretty straight-forward). Alternatively, if you only made it to a command line (CTRL+ALT+F1 drops you outside of the X-server and into virtual terminal 1), and you have a working internet connection,

```
sudo apt-get install xserver-xorg-video-intel
```

should work. Once it's done, reboot using sudo reboot.

---

### Post by ipodsmakezombies on 2009-08-14
Okay I'm trying this right now :) Thanks!

---

