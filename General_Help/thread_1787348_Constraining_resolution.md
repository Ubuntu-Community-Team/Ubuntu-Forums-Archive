---
title: "Constraining resolution"
date: 2011-06-21
forum: General Help
---

### Post by PenguinLust on 2011-06-21
I'm having a devil of a time trying to prevent this resolution which I think is overdriving my monitor. I'm able to get the resolution I want when I login, but when I reach the login screen, it's too high, and I don't know how to change that. Googling for advice just directs me to /etc/X11/xorg.conf but there isn't one and so far the only advice directed at me is to control grub's resolution, which, of course, does nothing because the login screen comes up well after grub.
I'm running 10.04.
Here's what I get from an lspci -v:
     >                                                  05:07.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core)
        Subsystem: Dell Device 01ae
        Flags: 66MHz, medium devsel
        BIST result: 00
        Memory at fc000000 (32-bit, prefetchable) [size=32M]
        Memory at fe6c0000 (32-bit, non-prefetchable) [size=256K]
        I/O ports at d880 [size=128]
        Expansion ROM at fe600000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: sisfb                      

---

### Post by wildmanne39 on 2011-06-21
> **PenguinLust said:**
> I'm having a devil of a time trying to prevent this resolution which I think is overdriving my monitor. I'm able to get the resolution I want when I login, but when I reach the login screen, it's too high, and I don't know how to change that. Googling for advice just directs me to /etc/X11/xorg.conf but there isn't one and so far the only advice directed at me is to control grub's resolution, which, of course, does nothing because the login screen comes up well after grub.
I'm running 10.04.
Here's what I get from an lspci -v:
Hi, you should have one. Type in terminal
```
sudo gedit
```hit enter, after it opens, open your file manager,click on file system, then etc, x11,xorgconf, then drag xorgconf to the open gedit window and you can change the file when you are done save and close gedit. Here are instructions for changing the xconf file.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
click on statically setup in xorgcong after you go to the link.

---

### Post by Grenage on 2011-06-21
You can either add an xrandr command to set the resolution as gnome starts up, or you can create an xorg.conf.  I would recommend adding the xrandr line.

I believe it would need to be entered in */etc/gdm/Init/Default*.  There's some good info [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html"), near the bottom of the entry.  You probably just need to set the mode, rather than add it:

```
xrandr --output VGA1 --mode 1024×768
```

You'd obviously change the res to whatever you wanted.

It's also worth mentioning that if any graphical tools are used (such as gedit), you would ideally use *gksu* rather than *sudo*.

---

### Post by PenguinLust on 2011-06-22
Ok, I've tried that now but it doesn't appear to have made a difference. Here's the beginning of my /etc/gdm/Init/Default

#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode

How do I create an xorg.conf from scratch?

---

### Post by Grenage on 2011-06-22
Is VGA1 the right port name?  If in doubt, post the output of:

```
xrandr -q
```

It's easy to verify the commands once you log in; just open a terminal and type or paste them there:

```
xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode
```

We can walk through an easy xorg.conf file if xrandr doesn't work (or regardless, it's your PC!).

---

### Post by PenguinLust on 2011-06-22
Oh oh, looks like it wasn't VGA1. What is it, "Screen 0"?
> Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1600 x 1200
default connected 1280x1024+0+0 0mm x 0mm
   1600x1200       0.0  
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
  1280x1024_60.00 (0x10d)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
I think we're getting somewhere. Now I can see that naughty maximum setting that I want to fix.

---

### Post by Grenage on 2011-06-22
I'm not overly familiar with xrandr, but from your output, I would imagine that it would be called 'default'.  I know that names tend to be down to drivers and the card being used, and I've never used one of those cards before. :)

---

### Post by PenguinLust on 2011-06-26
I changed them from "VGA1" to "default" but it hasn't made a difference.
   I'm wondering if the answer is in that maximum resolution thing. Is there a way to set that? The man pages for xrandr don't seem to indicate that. :(

---

### Post by Grenage on 2011-06-27
I'm guessing that default isn't something that can be referenced. :)

The max resolution will be modified when a mode is added, so that's something that must be happening after login.  The information I've looked at suggests that the SiS driver is used for that card, but that a separate one can be downloaded from the manufacturer's website.  It would need to be compiled.

At this point I'd like to say that when it comes to manually compiling and installing drivers, there is a much greater risk of something going wrong.  You could end up not being able to log in at all.

---

### Post by PenguinLust on 2011-06-28
Are you saying you don't know how to proceed, other than going through that epic task of building my own kernel?

---

### Post by Grenage on 2011-06-28
Whoah there, nobody said anything about kernel building - just drivers. ;)

You could try an xorg.conf to set the graphical settings, which should take effect at the login screen; unfortunately I don't know what driver that card is using.  I'm guessing that it's the SiS driver, but I can't be sure.

---

### Post by PenguinLust on 2011-06-28
Oh. Well driver building doesn't exactly sound like better-than-sex either. I can't believe it's this difficult to just set a resolution or forbid one.

So now my problem is that I don't know how to make an xorg.conf and you don't know my driver. How do I find out the latter? Would and lsmod help?
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6808  0 
vboxnetflt             18785  0 
vboxdrv               230432  3 vboxnetadp,vboxnetflt
abi_util               11599  0 
snd_ens1371            18910  3 
gameport                9089  1 snd_ens1371
snd_ac97_codec        100646  1 snd_ens1371
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
joydev                  8740  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_ens1371,snd_seq_midi
usblp                  10481  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
i3000_edac              2967  0 
snd                    54244  15 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
soundcore               6620  1 snd
lp                      7028  0 
dell_wmi                1793  0 
dcdbas                  5422  0 
vga16fb                11385  1 
serio_raw               3978  0 
vgastate                8961  1 vga16fb
snd_page_alloc          7076  1 snd_pcm
edac_core              37331  3 i3000_edac
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
tg3                   109324  0 
8139too                18545  0 
mii                     4381  1 8139too

---

