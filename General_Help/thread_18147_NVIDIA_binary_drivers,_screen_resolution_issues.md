---
title: "NVIDIA binary drivers, screen resolution issues"
date: 2005-03-04
forum: General Help
---

### Post by holomorph on 2005-03-04
There seems to be a lot of similar problems, but I haven't seen solutions that worked for me and have, I think, almost found one so hopefully this will be helpful to others and maybe someone can help me with the remaining issue:

I have a Toshiba P25, which is one of those 17" widescreen laptops, with an NVIDIA GeForce FX Go5200 card.  The native resolution  for this laptop is 1440x900.

I installed warty (of course) and overall it was beautiful; I'm very impressed with what works out of the box (I've been using Debian for several years now on other machines, but it didn't play well on this laptop).  Unfortunately, the resolution was not right, things were a bit stretched and too big.  So I hoped to fix it by installing the binary NVIDIA drivers.  That actually resulted in less resolution choices.  So I didn't bother messing around with it too much, upgraded to Hoary in hopes that Xorg would perform better.  

No luck right off the bat, but running 'sudo dpkg-reconfigure xserver-xorg' and just accepting everything (I think) did the trick; 1440x900 was now an option in the gnome resollution switcher and worked perfectly.  Unfortunately this left me using the 'nv' driver, so no hardware acceleration, not ideal.

I proceeded to re-configure with the 'nvidia' driver, but that destroyed my resolution, leaving me at like 1024x768 or something (with two lower options available).  A bit of digging in the log file reveals the problem; the nvidia driver was probing the EDID and resetting the hsync and vrefresh ranges to a maximum of 60, resulting in: 
(II) NVIDIA(0): Not using default mode "1440x900" (hsync out of range)

More digging in the forums lead me to Nvidia's readme file, in which I found the 
"IgnoreEDID" option.  Added the line:

        Option          "IgnoreEDID"            "true"

to the "Device" section of my xorg.conf file.   That *almost* fixed the problem.

Now if I stop gdm and run 'startx', the results are good.  The log says:
(**) NVIDIA(0): Option "IgnoreEDID" "true"
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Not probing EDIDs.
(II) NVIDIA(0): Generic Monitor: Using hsync range of 28.00-72.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz

I've omitted some lines here but basically I get the resolution I want.

What I don't undestand is if I run gdm the log makes no mention of the EDIDs at all:
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) NVIDIA(0): Generic Monitor: Using default hsync range of 29.00-55.00 kHz
(II) NVIDIA(0): Generic Monitor: Using default vrefresh range of 0.00-60.00 Hz

and then I get the line about hsync out of range for the resolution I want, and of course it's not available.  Any ideas why things are different running gdm and startx?


One othe thing that's been bugging me, is when I have the resolution working (say using the 'nv' software drivers) my gnome session refuses to use the correct resolution when I log in (though the login screen does use the correct one), and I have to manually change it every time.  Help on this point would be appriciated as well.

Bjorn

---

### Post by holomorph on 2005-03-05
It turns out all I needed was a reboot.  I donno what the problem was, but after shutting down last night, when I boot up this morning and gdm started (as usual) I had the correct resolution available.  Now if I could jusn get my gnome session to use that one by default.  

Just for clarification, in case someone else has the same problem, the way I got it to work is by [deleting /etc/X11/xorg.conf] running 'sudo dpkg-reconfigure xserver-xorg' and then accepting all of the suggested values, including using the software 'nv' driver.  This is important so that the probed values are correct later in the configuration.  I then edit /etc/X11/xorg.conf and replace "nv" with "nvidia", and add the line
```
         Option          "NoDDC"                 "true"
```
to the "Device" section (where the driver is specified.  Equivalently one could use "IgnoreEDID" instead of "NoDDC".  Then reboot.

---

### Post by holomorph on 2005-03-07
OK, I figured out how to fix gnome so it uses me preferred resolution by default. 
Applications-->System Tools-->Configuration editor, and then go to /desktop/gnome/screen/default/0 and edit the "resolution" key.  This "default" key had the wrong value, and was apparently the one being used.  /desktop/gnome/screen/shiver/0 had the correct resolution, but was obviously not being used when I started gnome from gdm, but was when I started via the startx script (shiver is the name of my computer).

---

