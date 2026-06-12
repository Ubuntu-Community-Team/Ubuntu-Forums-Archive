---
title: "Monitor not displaying GUI"
date: 2010-02-03
forum: General Help
---

### Post by CakeBomb on 2010-02-03
I've just installed Ubuntu 9.10 64 bit using Unetbootin, and I've managed to get into command line Ubuntu fine. I installed gnome (I think gnome, the command was "sudo apt-get install ubuntu-desktop"), typed "startx", and my monitor instantly went to a screen saying "NO SUPPORT". I rebooted, and this time a black screen with a white, low-resolution Ubuntu logo appeared for a few seconds, before "NO SUPPORT" appeared again. My graphics card is an ATI Radeon X1950XT AGP, and my "monitor" is a TV taking HDMI input through an adapter cable from a DVI out, if either of those pieces of info is useful.

I'm now back in command line Ubuntu having booted into recovery mode, and I'm using a text-only browser for the first time, so apologies if I've managed to miss any identical posts in my quick scan/search of the forums

---

### Post by CakeBomb on 2010-02-04
I've tried some more things, none of which has worked. I thought I should get straight in and mess with the video output settings for X.org, so I did some googling for possible solutions. 

First I ran sudo dpkg-reconfigure xserver-xorg, which did nothing.
I then found [this]("http://www.x.org/wiki/FAQVideoModes#ObtainingmodelinesfromWindowsprogramPowerStrip") helpful guide on how to get working modelines from within Windows. I tried to edit xorg.conf, but couldn't find it (it wasn't in /etc/X11).
I then rebooted in recovery mode and selected dpkg  Repair Broken Packages. This ran for a little while and did something to X11 (and a load of other things), and has added two options in GRUB. I haven't been able to find out what it's done to X11, because I now can't boot into anything, command line or otherwise. Booting into either of the recovery mode options I have now becomes unresponsive at the menu ([this screen]("http://2.bp.blogspot.com/_OA-pNGwN9sk/Sn79mIkBR0I/AAAAAAAAADY/hyDe7u2a-LE/s1600-h/recovery1.png")) and spews out text over it:

"One or more of the mounts listed in /etc/fstab cannot yet be mounted 
(ESC for recovery shell)
swap: waiting for /dev/mapper/cryptswap1
starting init crypto disks
*cryptswap1 (starting)
[20.880918] Intel AES-NI instructions are not detected
*cryptswap1 (started)"

I've left this for a few minutes but it seems to be stuck here.
When I try to boot using either standard option, rather than getting NO SUPPORT on my monitor I now get crazy unusable disco Ubuntu, where everything is random sometimes-flashing colours and I seem to be looking at the zoomed in top left quarter of a screen. There are sometimes semi-readable windows which are oddly sized and heavily interlaced with random bars of colour (I just barely managed to log in and shut down). The good news: the mouse cursor displays perfectly! Though it is about 3 times the size it should be...

---

### Post by stoneage on 2010-02-04
If you haven't already, install graphics drivers for your card.
The no support message suggests the monitor resolution is not supported.

Ubuntu uses hal now instead of xorg.conf, but for custom settings you can create one and save it to /etc/X11

I can't help you with the mount problem, sorry.

---

### Post by Mark Phelps on 2010-02-04
You're not going to be able to install ATI drivers for your card -- because there are none that will work with your card and Ubuntu 9.10.  The last Ubuntu version that would work with your card and ATI drivers was 8.10.

Follow the directions in the link below to remove any ATI drivers and replace them with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by CakeBomb on 2010-02-04
Things are looking up - I'm posting from firefox in gnome! Not quite perfect yet, but here are the steps taken so far in case this can be of any help to anyone:

First I solved my problem with actually getting into a command line properly with the help of [this page]("http://benste.blogspot.com/2009/10/problems-in-karmic-due-to-use-of.html") - apparently I shouldn't have chosen to encrypt my home directory at install. Before that, I'd had to run a normal startup and press Ctrl + Alt + F1 to get to a command prompt, at which point Xorg kept throwing up errors when I tried to run Xorg -configure. Now I can get into command prompt through recovery mode without any errors, which let me run Xorg -configure to create an xorg.conf in my home directory. I edited this to include the modeline I got from powerstrip, restarted, and I've now got a GUI :D

But... I can only see the centre of the screen. There's probably 100px on every side that's off the screen, the resolution is huge. I've tried running xrandr --output Monitor0 --scale 1.1x1.1 but nothing happens. I don't really just want to scale in xrandr anyway, because the screen's flickering a lot at this setting - at this point I think I'm going to go back into windows and copy down a load of modelines for different display settings, then try them out and see what works. Is there any better way of doing this from ubuntu, are there any advanced display options I haven't been able to find or anything?


Stoneage: what is hal, and how do I use it to change my display settings? I've had a google but I can't find any useful info.

Mark: I assume the fact that I've now got a semi-working display (high resolution, full colour) means that I'm OK on the driver front? I haven't tried to install the ATI drivers at any point.

Thank you both!

---

### Post by stoneage on 2010-02-04
I don't honestly know much about hal, google is your best bet. I found these:-

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

