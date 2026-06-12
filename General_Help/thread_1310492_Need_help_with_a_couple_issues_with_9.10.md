---
title: "Need help with a couple issues with 9.10?"
date: 2009-11-01
forum: General Help
---

### Post by tryingtoboot on 2009-11-01
I just installed 9.10. First problem, the monitor is 1680x1050 but the computer thinks it's 1680x1200 (or something like that). And when I tried to enable some basic desktop effects, it said it couldn't be enabled (it's integrated intel graphics, I know I tried a version of Ubuntu or some other kind of Linux on this computer a long time ago and it worked). So how do I fix that video issues?

Second, I'm trying to edit grub to make XP default (especially since there's video problems with Ubuntu right now). I run gksudo gedit /boot/grub/menu.lst or equivalent and it just looks empty. I've edited grub in the past...
UPDATE: I think I understand the issue, 9.10 uses Grub2. I'm working on that one myself...

Still need help with how to get the video working properly!

---

### Post by Wielkitb on 2009-11-01
Yeah, the former /boot/grub/menu.lst is now split into two: **/boot/grub/grub.cfg** and **/etc/default/grub**.
The first one helds the "core" and the other one is the header of old menu.lst. From there on, I think you'll find your way ;)

About the screen resolution, the most usual way is to edit your Xorg.conf file. Some people are complaining about it, because its structure is apparently different if compared to older releases... but give it a try.

---

### Post by TheForumTroll on 2009-11-01
> **Wielkitb said:**
> Yeah, the former /boot/grub/menu.lst is now split into two: **/boot/grub/grub.cfg** and **/etc/default/grub**.



No, grub.cfg is automatically created and shouldn't be changed. You need to update the files in /etc/grub.d/ and /etc/default/grub instead and then run update-grub.

---

### Post by Wielkitb on 2009-11-01
> **TheForumTroll said:**
> No, grub.cfg is automatically created and shouldn't be changed. You need to update the files in /etc/grub.d/ instead and then run update-grub.

Really!? Good to know.
I changed it by myself... it worked, but now I see it's not the proper way to do it.

Sorry about the misinformation!

---

### Post by tryingtoboot on 2009-11-01
I got the boot order fixed with some tool I got in sudo apt-get install... already forgot the name, lol.

REAL PROBLEM THOUGH: I need clearer instructions than to edit Xorg, I need step-by-step. I'm not such an expert in the terminal... I don't have a huge amount of Linux experience. If it makes a difference, I chose the safe-graphics-mode when I first booted into the CD before loading the live cd desktop (because I was having a problem before, not sure if what I did was the solution though).

And I have two other issues I need help with too:

When I turn off Ubuntu, I get a black terminal-like screen that has the username and "ttyl" or something at the top and it says like it has shut off or something, but I need to actually press the power button before it finishes shutting down. How do I make it so this is automatic?

And, how do I make it so the screen doesn't lock after the computer is in standby?

Just for context, I'm trying to set up this Linux partition so my Dad will use it instead of Windows XP. I'd like to get it working right. ;)

---

### Post by TheForumTroll on 2009-11-01
Yes but any changes to /boot/grub/grub.cfg will be overwritten by update-grub. Like when installing a new kernel :)

---

### Post by TheForumTroll on 2009-11-01
Changing the resolution in System -> Screen (i think - mine isn't in English. If not run "gnome-display-properties") doesn't work?

---

### Post by tryingtoboot on 2009-11-01
> **TheForumTroll said:**
> Changing the resolution in System -> Screen (i think - mine isn't in English. If not run "gnome-display-properties") doesn't work?
When I try to change the resolution, 1680x1050 is not one of the choices listed! And like I said it's obviously not properly reading the video driver because it won't let me set any desktop effects. I had this problem with Linux Mint 9.04 but I thought the problem would go away when I removed that and installed Ubuntu 9.10.

---

### Post by TheForumTroll on 2009-11-01
Is the correct vga card shown in the list with:

```
lspci -v | less
```

It will also tell what kernel driver and modules is used.

---

### Post by tryingtoboot on 2009-11-01
> **TheForumTroll said:**
> Is the correct vga card shown in the list with:

```
lspci -v | less
```It will also tell what kernel driver and modules is used.

It's currently in XP so I can't check, but for reference, according to XP:
Chip Type: Intel 82845G Graphics Controller
Memory Size: 64 MB
Adapter String: Intel 82845G GL/GE/PE/GV controller

---

### Post by tryingtoboot on 2009-11-01
> **TheForumTroll said:**
> Is the correct vga card shown in the list with:

```
lspci -v | less
```It will also tell what kernel driver and modules is used.

It says: 

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
        Subsystem: Micro-Star International Co., Ltd. Device 5770
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
        Subsystem: Micro-Star International Co., Ltd. Device 5778
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at ee000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>
        Kernel modules: i915

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
        Subsystem: Micro-Star International Co., Ltd. Device 5770
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at d800 [size=32]
:

----
So it looks like it's correct, right? Now, I checked Google and it looks like there are some problems with the 82845G, but there are work arounds like editing Xorg. I have no idea where to begin with that, so could someone help me with that, step-by-step to fix the problem (preferably in such a way that doesn't render X useless because I don't want to have to reinstall)?

I've also decided that it would be better if I would limit this thread to just my display/video/driver problem. Screen locking and incomplete shutdown are at [http://ubuntuforums.org/showthread.php?p=8220300](http://ubuntuforums.org/showthread.php?p=8220300) and [http://ubuntuforums.org/showthread.php?t=1310643](http://ubuntuforums.org/showthread.php?t=1310643)

---

### Post by TheForumTroll on 2009-11-02
Yeah I'm not that happy to play around with Xorg myself.

I found [this post]("http://ubuntuforums.org/showpost.php?p=1964142&postcount=3"). Not sure if it is any help though.

---

### Post by tryingtoboot on 2009-11-02
> **TheForumTroll said:**
> Yeah I'm not that happy to play around with Xorg myself.

I found [this post]("http://ubuntuforums.org/showpost.php?p=1964142&postcount=3"). Not sure if it is any help though.
It says "Intel 815/852/855," is that for my particular configuration? And if I do that, will it fix it?

Does anyone know what I should do? It's not like the a1010n isn't mainstream... I just need someone who knows what they're doing more than me to tell me how to fix this video issue.

---

### Post by TheForumTroll on 2009-11-02
The download page says it is for "82830M, **82845G**, 82852GM, 82855GM, 82865G, and 82915G/GM".

> **tryingtoboot said:**
> 

00:02.0 VGA compatible controller: **Intel Corporation 82845G/GL**[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
        Subsystem: Micro-Star International Co., Ltd. Device 5778
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at ee000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>
        Kernel modules: i915



---

### Post by tryingtoboot on 2009-11-02
Installing the 915 drivers from Intel as per that post didn't fix anything.

Other suggestions to get this working?

Be honest, if I install OpenSUSE 11.2, will it have this problem? I'm having trouble getting into the LiveCD but I am able to install it... I just want to know if it would be a waste of time.

UPDATE: Ok, you know what? This is becoming a huge waste of time. Ubuntu 9.10 obviously isn't the OS for me if it can't recognize my mainstream hardware. Will try openSUSE, will report if it works or if Linux in general officially sucks.

UPDATE 2: openSUSE didn't work right either... I think the HP a1010n is just a really hard computer to get Linux onto.

---

### Post by Dark9204 on 2009-11-02
Is it really that hard to just edit the X.org config?

Here is an example:

Run sudo gedit /etc/X11/xorg.conf

now edit the file.
Example:

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768_60.00"
    EndSubSection
EndSection

Hope this solves your problem?

A note: The intel drivers for linux are not that great, go blame intel for this.

---

### Post by tryingtoboot on 2009-11-02
> **Dark9204 said:**
> Is it really that hard to just edit the X.org config?

Here is an example:

Run sudo gedit /etc/X11/xorg.conf

now edit the file.
Example:

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768_60.00"
    EndSubSection
EndSection

Hope this solves your problem?

A note: The intel drivers for linux are not that great, go blame intel for this.
Two things.

First, an example of xorg doesn't tell me how I'm supposed to write it up.

Second, I apologize. I think it's more an issue of the HP a1010n sucking than Linux. Seems like a terrible computer for Linux.

---

### Post by TheForumTroll on 2009-11-03
Maybe if you post your Xorg config someone can tell you what to change.

---

### Post by tryingtoboot on 2009-11-03
> **TheForumTroll said:**
> Maybe if you post your Xorg config someone can tell you what to change.
The xorg was like barebones, it just said vesa or something and not much else. Anyways I found an older version of Linux Mint that actually works with the vid card so now I'm good. For that issue at least ;)

---

