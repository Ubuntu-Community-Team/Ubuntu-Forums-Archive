---
title: "screen resolution"
date: 2011-03-03
forum: General Help
---

### Post by canhoto on 2011-03-03
I have a good Asus monitor in which I can have a resolution of 1280x800 when using Mac Os (I have a Power Mac G4). However, when I try to have a better resolution with Ubuntu, the only resolution that it lets me choose is 800x600! There are no choices. I tried the "detect display" button but it doesn't change anything.

Any ideas?

---

### Post by TeoBigusGeekus on 2011-03-03
What's your graphics card?
```
lshw -c display
```
Have you installed any proprietary drivers for it?

---

### Post by canhoto on 2011-03-03
it says:

description: VGA compatible controller
product: Rage 128 PF/PRO AGP 4x TMDS
vendor: ATI Technologies Inc
physical id: 10
bus info: pci@0000:00:10.0
version: 00
width: 32 bits
clock: 66 Mhz
capabilities: vga_controller bus_master cap_list
configuration: driver=aty128fb latency=255 mingnt=8 module=aty128fb

As for the drivers, apparently not. At least there are no drivers listed on the "Hardware Drivers"

---

### Post by TeoBigusGeekus on 2011-03-03
After a quick googling, it doesn't look good:
[http://ubuntuforums.org/showthread.php?t=1122749]("http://ubuntuforums.org/showthread.php?t=1122749")

You could try [this]("http://manpages.ubuntu.com/manpages/maverick/man4/r128.4.html") as well.

---

### Post by canhoto on 2011-03-04
> You could try [this]("http://manpages.ubuntu.com/manpages/maverick/man4/r128.4.html") as well.

How do I install that?

I'm trying to run Linux (Ubuntu) for a couple of weeks on my Power Mac. I really would like to use it instead of Mac OS. But I'm affraid I won't, because of this display thing. It's really awful. So, I would appreciate some help.

Thanks

---

### Post by TeoBigusGeekus on 2011-03-04
I think you should
```
chmod +x /path/file
```
to make it executable and then
```
sudo ./file
```
to execute it.

---

### Post by canhoto on 2011-03-04
Sorry. It didn't work. I couldn't install it.

---

### Post by canhoto on 2011-03-07
I also installed the Ubuntu in an iBook. It worked fine and I have Ubuntu 10.04 LTS (I think) running.

The problem keeps the same: it shows only the 800x600, or the 600x480 options. Actually, it uses only part of the display: I see part of the display on black and the repetition of part of the desktop image below the main one!
 I even managed to install the drive you suggested (  r128  ). But it doesn't change. Should I install another drive for this iBook? My graphics card info is the following:
>   description: VGA compatible controller
       product: Rage Mobility M3 AGP 2x
       vendor: ATI Technologies Inc
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=aty128fb latency=255 mingnt=8
       resources: irq:48 memory:94000000-97ffffff(prefetchable) ioport:400(size=256) memory:90000000-90003fff memory:90020000-9003ffff(prefetchable)
Any help would be welcome...

---

### Post by canhoto on 2011-03-11
> **canhoto said:**
> I also installed the Ubuntu in an iBook. It worked fine and I have Ubuntu 10.04 LTS (I think) running.

The problem keeps the same: it shows only the 800x600, or the 600x480 options. Actually, it uses only part of the display: I see part of the display on black and the repetition of part of the desktop image below the main one!
 I even managed to install the drive you suggested (  r128  ). But it doesn't change. Should I install another drive for this iBook? My graphics card info is the following:
Any help would be welcome...

Any help with this, please?

---

