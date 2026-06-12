---
title: "No Disk Booting."
date: 2011-07-17
forum: General Help
---

### Post by kingnube1 on 2011-07-17
So I have been meaning to completely wipe my Hard Disk here lately, but I have ran into a problem. My computer will no longer boot from disk, I have the Boot Priorities set correctly but for some reason it just goes straight to my Hard Disk. It won't even Boot off of a Flash Drive. This all really started happening after I upgraded to 11.04.

---

### Post by DawieS on 2011-07-17
Welcome to the forums:smile:
1) Check in your BIOS whether your CD/DVD ROM is picked up during boot-time (You have to press some key when booting, check your screen).
2) Check the Boot Sequence to boot from CD first.
3) Insert the Live CD, or other bootable CD/DVD, and reboot (If the CD image does NOT contain a valid boot segment, the BIOS will skip the CD, and boot from the next selection in the boot sequence).
If you are sure that it is a valid bootable CD, but still don't boot, then maybe your CD is damaged, or the laser pick-up is dirty.

Have you tried other bootable CD's?
Have you tried having ONLY the CD ROM in the boot sequence, disabling the others?

---

### Post by Blasphemist on 2011-07-17
There is also a boot manager option when you first see anything on the screen, on many pc's at least. On my Toshiba I press F12 to access it. I can then choose the boot device.

Did you burn the iso to the cd and usb that you tried. The image must be burned to the disk not copied.

I'm not trying to be insulting it's just that something like this that doesn't seem to be working as designed usually points to a basic thing being overlooked.

---

### Post by kingnube1 on 2011-07-17
No it's not insulting I understand, my computer was Custom Built and the BIOS is not the usual Phoenix, it was done by Asus if I recall correctly. I have tried (Before hand) everything else except only making the CD the only thing that should boot, but also when ever my computer start's to Boot the light's do not flicker like they should be even if they are not being booted. They work when Ubuntu has booted up and I am on the Desktop. I know the CD is not damaged, I thought it could have been but I tried it on another PC and it booted just fine.

---

### Post by Blasphemist on 2011-07-17
Good, that's good information. From that I'd say, try a usb. :D

Seriously, if you go into bios and it's boot settings, is the optical drive an option? If it is, and it's first in order, and it works after boot, I wonder about this bios. When you are in the bios check it's brand and version. Then check for updates from your pc vendor. If they have none, check the bios vendor. Be very careful to understand the update process before doing an update. Don't want to blow the thing up you know.

You might also check with microsoft to see if you could get a usb key to install. Or, you could in theory get an external dvd connected via usb and try that. If you had to buy one and it didn't work for this for some reason (I do think it would), return it.

Anyway, just some more idea's.

---

### Post by kingnube1 on 2011-07-17
I have already tried the usb idea :(, I am honestly confused by this whole thing. I cannot even boot the Live cd. Everything is up to date I know that for a fact, I did that not too long ago. I also have one more question if you do not mind. I have a .IMG file of Google's OS and I was wondering if there was a converter to .ISO I could use, or what to type into the Terminal so I could just mount it and extract it. I have seen other Threads with this same question but not a lot of the information that I have found has come to a happy ending.

---

### Post by Blasphemist on 2011-07-17
I think the google image thing would depend on a few things. What hardware did it come from and what was used to make the image. If you had similar enough hardware and a program that restore that image, it could maybe possibly work. Lot's of ifs though. It would have to restored not installed and might well never work.

---

### Post by wildmanne39 on 2011-07-17
Hi, you might try resetting your cmos that will clear all setting then you can set up your bios configuration again. The cmos has a little jumper that you switch to reset cmos then put it back the way it was, you can google for what it looks like.

---

