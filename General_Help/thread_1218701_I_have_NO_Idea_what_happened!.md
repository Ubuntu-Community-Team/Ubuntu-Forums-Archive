---
title: "I have *NO* Idea what happened!"
date: 2009-07-20
forum: General Help
---

### Post by Sanus Compleo on 2009-07-20
Good LORD, I'm frustrated.  Several problems occurred today, when I installed the "Toribash Linux Client", ran fine, played a little while, and I ran into the trouble when I tried to exit out.  It froze my computer COMPLETELY.  I couldn't move the mouse, I couldn't do anything.  I tried to turn it off with the power button, nothing, so I unplugged it from it's AC Adapter, and I took the battery out.  Let it reboot, it came up with "Your video card/driver/monitor could not be detected, you will have to reconfigure these yourself". I continued through with "Run Ubuntu in Low Graphic Mode", or what have you.  Also dpkg-reconfigure xserver-xorg (Or whatever the proper command for this is) did NOT detect my settings, tried with no success to reinstall my ATI driver, still nothing.  Also I cannot open several applications, Kmuddy and Toribash being two that I have found so far.

What I'm running:
Intrepid Ibex,
Dell Inspiron 600m
ATI Radeon RV250 (Firegl 9000)

I also have a second monitor (Hp l1925) that's normally hooked up, though now since Ubuntu cannot detect monitors (On Screen Resolution Display, I get a big fat "Unknown" for my Laptop's display!).  Can somebody please help?

---

### Post by earthpigg on 2009-07-20
what happens if you boot from a live cd?

i suggest trying a few: we know 8.10 works, but give 8.04 and 9.04 a shot just for good measure.

---

### Post by philcamlin on 2009-07-20
boot into recovery mode and remove it

---

### Post by Sanus Compleo on 2009-07-21
I have no liveCD, and I already removed the game, going to try to get it to work right later I suppose.  Problem is, (I'm pretty sure) is with Xorg, it's cleared out.  Has nothing at all in it to do with my graphic card.  Can't detect any sort of... anything.  Gets a nice little "kitid: No resume image" or something error right before it goes to a neat little warning box with "HEY, You screwed up" on it.

---

### Post by Sanus Compleo on 2009-07-21
Okay, I see that "Kinit: No resume image" is just a normal boot thing, that's supposed to show up, meaning that I wasn't hibernating.  Going to grab my logs from Xorg, they have something about a Signal 11 shown, so it kills the process or something stupid?

---

### Post by earthpigg on 2009-07-21
> **Sanus Compleo said:**
> I have no liveCD, 

the first step of 95% of Ubuntu problems is popping a live cd in to confirm that it isn't a hardware failure.

get a live cd, friend :)

---

### Post by philcamlin on 2009-07-21
> **earthpigg said:**
> the first step of 95% of Ubuntu problems is popping a live cd in to confirm that it isn't a hardware failure.

get a live cd, friend :)
always a good idea :)

also if i ever wanna see if it will work on a new pc too i pop it in and check how it will work

---

### Post by Sanus Compleo on 2009-07-21
I don't think that this is a hardware error, because if it were a hardware error, that would mean it would be in the video card, which would mean I wouldn't be able to USE my computer.

---

### Post by earthpigg on 2009-07-21
> **Sanus Compleo said:**
> I don't think that this is a hardware error, because if it were a hardware error, that would mean it would be in the video card, which would mean I wouldn't be able to USE my computer.

ok, then lets consider something else you could get from a live cd:

Ubuntu, functioning properly.

the difference between the live environment and an install, in some regards, is not very significant. you can sudo apt-get install, you can enable proprietary drivers then restart X for it to take effect and see if they work, etc, etc. maybe one driver breaks the live CD enviornment, and another doesn't? only one way to find out!

its a sandbox you can break, try, and test things out in without risking further damage to your main install.

if you can find a pattern to what exactly breaks Ubuntu, you will know what your problem is on your hard drive install.

Live CDs rock.

---

### Post by Sanus Compleo on 2009-07-21
Looking through my startup logs, I seem to get the big error Here:

"error setting MTRR (base = 0xe8000000, size = 0x01ff0000, type = 1) Invalid argument (22)"

Looking through Xorg logs, all looks hunky dory until this:

```

(II) VESA(0): Total Memory: 511 64KB banks (32704kB)
(II) VESA(0): Configured Monitor: Using hsync value of 48.36 kHz
(II) VESA(0): Configured Monitor: Using vrefresh value of 60.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): Display dimensions: (290, 210) mm

```

And then there's this:

"(II) VESA(0): VBESetVBEMode failed...Tried again without customized values."

EDIT(After seeing Earthpigg's post):
Fiiiiine.  I'll get a LiveCD.  When I can get a blank CD, or in two weeks through the mail.

EDIT2:
When trying to start Toribash, I get this in the Console:

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11

```



EDIT 3:
And the Xorg log BEFORE it goes into low graphics mode:

```

(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3019]
1: [0xb80d0400]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b4ac27]
3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b1855a]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7b1b4fc]
5: /usr/X11R6/bin/X(InitOutput+0x96f) [0x80aac9f]
6: /usr/X11R6/bin/X(main+0x279) [0x8071b19]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7cd0685]
8: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.

```

---

### Post by Sanus Compleo on 2009-07-21
SOLVED, turns out I had the wrong driver.  For anyone else who gets this problem, try a

"sudo apt-get remove --purge xorg-driver-fglrx "

That's what fixed me.

---

