---
title: "Slow Bios"
date: 2009-09-03
forum: General Help
---

### Post by confused! on 2009-09-03
Hi - installed ubuntu on laptop over a year ago to dual boot with vista (an evil necessity). Pre install bios loaded in the sub 10 sec region - immediately after install bios started taking 22 secs. Have spent a year updating to new bios releases and fiddling as much as possible with what is a very limited settings menu. Bios still takes 22 secs. After all my fiddling i reckon its looking for something - or getting confused by what it's finding on the hard drive. I've done a couple of fresh installs since to no avail. even on one occasion just installing vista. playing with the boot order doesnt really seem to help either. I am now hellaconfused and verging on giving up. any ideas? ps i tried boot and nuking the drive pre fresh install.

---

### Post by dandnsmith on 2009-09-03
Is this 22 secs the time taken to get up the POST results, and then progress to GRUB - or are you including something else?

I've seen delays before starting GRUB when a 'DMI pool' message comes up, and also when the HDD has a problem (you could unplug it to check the latter).

Have you also installed any added cards, USB ports ...?

---

### Post by confused! on 2009-09-03
The 22 secs includes the POST and then the time taken by the bios start up. Once in grub all seems gravy. additional note is if i hit the startup or boot order f-keys then its about 15 secs from bios start up to loading those menus. and no - its all still running with the factory installed bits.

thanks for the quick reply!

p.s vostro 1310 - newest bios (A15 off the top of my head)

---

### Post by CatKiller on 2009-09-03
> **confused! said:**
> The 22 secs includes the POST and then the time taken by the bios start up. Once in grub all seems gravy.

It seems that the delay starting at the same time you installed Ubuntu was just coincidence, then. Linux has no control over the boot process before GRUB actually loads it.

Some BIOSes have a "Quick Boot" option that turns off some of the startup checks; only testing the existence of the RAM once, that kind of thing. You might be right in thinking that the BIOS is looking for something. Changing settings from "Auto" to the appropriate value may help; hard drive auto-detection and the like. It's also possible that it's looking for a network-boot image to use. Turning off anything like that might help.

---

### Post by confused! on 2009-09-03
Hi - I've goofed about with all the enable/disable features I could inside the bios settings over the last few months- unfortunately the options of what are changeable seem limited in comparrisson to some other versions (ie not option to change bus setting etc.) i cycled through all network wake options and quickboot etc turning on/off one by one and trying different combos but didn't really change anything....  I looked about a bit and found one post in another thread that said some bios settings could be changed from inside linux - though i had never fiddled that deep when the problem arose. Other suggestions suggeseted boot sector virus but i doubt i've got one (nuked the drive). Vista has occassional fits and needs to be repaired - claiming something is wrong with the start up - this is normally fixed through some hidden-from-user-mysterious-scrolling-bar available from dvd boot. maybe i've just systematically made the same mistake when installing and reinstalling and the bootsector is a mess. anyone know any diagnostic checks/links to what it should look like? Note: osx86 is on another partition and seems just as happy as linux to boot (not asking for help with windows - it still boots and i wouldnt dare :D)

---

### Post by P4man on 2009-09-03
did you perhaps add a drive? maybe the bios is struggling detecting your drives. Maybe a cabling or master/slave issue? For sure its not  linux (or OS-X or windows) thats to blame here. How I **wish** linux could actually change bios settings and flash biosses on most computers :)

---

### Post by confused! on 2009-09-03
hi - no, not made any hardware changes - problem began immediately after partitioning drive and installing ubuntu. haven't been able to reduce the bios loading time since...

---

### Post by NoaHall on 2009-09-03
Try moving your harddrive with GRUB on to the top of your boot list - this way, it won't check anything else to boot.

---

### Post by confused! on 2009-09-04
Only one hard drive and its already on top.
Looking at a verbose-esque bios loading screen - the delay seems to be after the shadowing before the hard drive is loaded. I am now next to convinced its looking for something....

---

### Post by CatKiller on 2009-09-04
> **confused! said:**
> the delay seems to be after the shadowing

I don't think you need Video or BIOS shadowing on unless you're running DOS. I don't think modern OSes use the ROMs for anything.

---

### Post by confused! on 2009-09-04
I'll try and turn it off then - but not all together sure what it comes under. Trial and error time ! :D

---

