---
title: "Removed video card to switch to onboard video, now cannot start kdm"
date: 2011-06-19
forum: General Help
---

### Post by misterbk on 2011-06-19
Hi all,

Got a bit of a problem where xorg can't start kdm.  I pulled out a dying AGP card to try and switch to onboard video, and I think the previous configuration is gumming up the works.

I've been running this system for quite a while, as you'll be able to tell from the version numbers.  Here's the system configuration:

ATI all-in-wonder radeon 9000  <-- having problems, removed it
32-bit AMD athlon 2400+ or something (old single-core Athlon)
Onboard VGA from VIA VT8378
Kubuntu 8.04.1  (lol)

For the onboard video, here's the lspci:
VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


     **This is what I did:**
This system is just an mp3 jukebox console that plays music and runs samba / apache, which is why everything's so old...  I never needed to mess with it.

The Radeon fan failed over two years ago, and since then the card has been hot enough to cook on, but has kept running.  Recently, a power outage killed the monitor attached to it (of all things) and I had to get a new screen.  Well, old screen was square, and you can't buy anything but widescreen now.  Had trouble getting the Radeon to choose a widescreen resolution, so I decided it was time to remove it.  There were some other issues anyway, like power save never turning off the backlight.

So, I removed the ATI AGP video card, to switch to onboard video.  All I did was shut down, yank the card, plug a VGA cable to the onboard video and reboot.

**So far, not working:**
After reboot, kdm-kde4 can't start.  It tries to start but just goes into the text-only CLI.  It seems like it finds the widescreen video modes I was after but ends up spitting this error to logs:

```
(II) VESA(0): Searching for matching VESA mode(s):

(II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
(EE) VESA(0): No matching modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```


**What I've tried so far, all as root of course, and not in that order:**

 dpkg-reconfigure xserver-xorg
 dpkg-reconfigure -phigh xserver-xorg 

/etc/init.d/kdm-kde4 stop
/etc/init.d/kdm-kde4 start


dpkg-reconfigure sent me through a text-mode pseudo-menu thingy that defined my keyboard layout and all that nonsense, and then left the system in exactly the same state.

I poked around on Google and the only info I could find was irrelevant, mostly related to those horrible manual-install nvidia drivers from back in the ubuntu 7 days.



**What I really want to do:**

What I'm really after is to get widescreen resolutions and power-save working on the new screen.  I can pop the ATI card back in, it's just on its last legs and I'd be happy to lose the extra wattage.  The power save issue has been there for a while, the ATI card did not suspend the screen.  It sent faint stripes of gray instead of a blank screen and the backlight stayed on forever.

Obviously, not too keen on buying a replacement AGP card.

Would like to avoid having to transport my Amarok databases to a new server.  I make heavy use of the song ratings and whenever I try to transport the database from the old system to a fresh build I have to spend hours relearning sql commands.


Any ideas how to either fix the resolutions on the ATI or (preferably) get KDE to start on the onboard graphics?

---

### Post by christopher.wortman on 2011-06-19
Pop ATI card and go into Konsole, and type 

sudo apt-get remove --purge xorg-driver-fglrx fglrx*

Reboot the system with the ATI card still in the system, when you get to the desktop, shut the computer down and remove the card, turn the system back on and see if you get to KDM, if it drops you to terminal, 

sudo dpkg-reconfigure xserver-xorg

when it has run it's course, reboot the system by typing

sudo shutdown -r

If all this fails, reinstall from Kubuntu disk.

---

### Post by misterbk on 2011-06-19
Worth a try!  Was going to pop the card back in anyway, to get it back to playing mp3s again.

Couple of things:

* I never took steps to install the fglrx driver.  I guess that's default nowadays?

* If I reinstall, I'll have to migrate that amarok database which is always super annoying.


Would a dist-upgrade be a good thing to try, or is it pushing it to go forward that far?  (might lose the amarok database that way just as easily.)  The amarok database is stored in postgresql.

EDIT:  Also I do currently have access to the system.  It's booted up right now, just no gui.  I'm shelled in from a windows box.  Could I just remove fglrx from here, or is that not safe?

---

### Post by misterbk on 2011-06-19
Upon closer inspection, there are no fglrx packages installed at all.

Maybe this is why the video card isn't seeing the resolutions?  I see in Xorg.0.log that the monitor returned its EDID info and the vidcard only checked it against 640x480, 800x600 and 1024x768.

It's using this vesa driver.  Is that right?:

```

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 2.0

[ ... ]

(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
```

Starting to think the resolution issue might be fixable on the radeon. Here are the screen modes from the monitor's edid info:

```
(II) VESA(0): EDID vendor "ACR", prod id 523
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)

[ ... more modes ... ]

(II) VESA(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) VESA(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) VESA(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1600x900"x59.9  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync (56.0 kHz)

```

And here's the corresponding list from the vidcard support list:

```
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x870@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #3: hsize: 1600  vsize 900  refresh: 60  vid: 49321
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 50  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 160 MHz
(II) VESA(0): Serial No: LR4080114210
(II) VESA(0): Monitor name: Acer S202HL

```

Maybe I can turn one of those on?


EDIT:  lspci for vidcard, since it's plugged in now:

01:00.0 VGA compatible controller: ATI Technologies Inc R200 BB [Radeon All in Wonder 8500DV]

---

