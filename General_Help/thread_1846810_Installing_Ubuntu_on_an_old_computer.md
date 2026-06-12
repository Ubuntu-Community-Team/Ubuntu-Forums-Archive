---
title: "Installing Ubuntu on an old computer"
date: 2011-09-19
forum: General Help
---

### Post by derelict_space on 2011-09-19
alright, so i've never installed ubuntu before on anything, so bare with me on this. here's the situation:

i found an old computer in my parent's basement and i want to install ubuntu on it. the computer used to have windows xp installed on it, but at the moment when i turn it on, it states the manufacturer and then proceeds to a black screen with a blinking underscore in the upper left corner. i did a little searching and apparently that means something's wrong with the boot drive or boot something.

from here, i just want to install ubuntu on this computer using a usb drive. i tried putting the ubuntu files on a usb drive and plugging that into the computer, but the computer doesn't seem to acknowledge the usb drive. any help would be greatly appreciated.

---

### Post by MG&amp;TL on 2011-09-19
Could you tell us the specs of said computer?

If a USB won't work, try a cd. (On my computer, which is OLD, USB won't work.)

And if it's REALLY old, try Xubuntu or Lubuntu, rather than Ubuntu.

---

### Post by seawolf167 on 2011-09-19
Easiest way to check is to download a Ubuntu live cd and boot off of it to see if everything works - my guess is it you found it in your parents basement and it had Windows XP on it you may need a lighter distro such as Xubuntu / Lubuntu as previously stated.

Also - if you hit [F2] (sometime its [ESC] or [F10]) while the computer is turning on (during POST) you can enter BIOS and from there get among other things, the processor speed/make/model, the amount of RAM and its speed, etc. Additionally, you should be able to check the S.M.A.R.T. status of the [any] internal hard drives to see if they are working properly.

---

### Post by derelict_space on 2011-09-19
alright, so i got the bios open. the computer is a compaq presario 5000, it has 512 mb memory. as a matter of convenience i really would like to use a usb drive for this, because i have one of those on hand but i don't have any cds. is there any other information from the bios i should grab to help figure this out?

---

### Post by mörgæs on 2011-09-19
> **derelict_space said:**
> I tried putting the ubuntu files on a usb drive and plugging that into the computer, but the computer doesn't seem to acknowledge the usb drive.

Copying files to the USB stick is not enough. The stick must be created with a program like **Unetbootin** in order to work.

While you are in there, pay attention to the version number of the BIOS. Maybe it is time for upgrading BIOS.

---

### Post by derelict_space on 2011-09-19
there was a set of instructions on the ubuntu website when i downloaded the iso. there was a program i ran that had me point out the iso and what drive the usb was in. i didn't just plop the iso into the usb drive. was there more that i needed to do?

---

### Post by seawolf167 on 2011-09-19
Well you definitely want to use either Xubuntu or Lubuntu on that computer as it is old enough to do so. In order to boot off a USB, head over to [UNetbootin ]("http://unetbootin.sourceforge.net/")and use you computer and a downloaded Ubuntu .iso file to make a bootable USB drive.

You'll need to ensure in BIOS that USB booting is enabled and has a higher priority than the hard drive. You should also have the option when booting to press some key to get a boot menu where you can select which device to boot off of (i.e. hard drive, cd, usb)

---

### Post by Paddy Landau on 2011-09-19
For a computer with such low specs, I most certainly would go with [Lubuntu](http:lubuntu.net).

---

### Post by MG&amp;TL on 2011-09-19
Some computers (like mine) do not support 'permament booting' i.e. setting it to a higher priority, therefore you have a boot menu, from whence you can choose what to boot from. It may give a system beep if it boots successfully to the USB.

And if nothing seems to happen, but the CPU light is on, and the screen is backlit, that seems to happen sometimes on the old hardware I've tried, wait long enough and the install/try screen should show up.

---

### Post by derelict_space on 2011-09-19
alright, so install lubuntu. noted. okay, so in the bios, in the boot manager, it lists: cd-drive, floppy drive then hard drive. am i totally out of luck with the usb drive or is there any way to make a usb work? the light on the usb drive also doesn't light up when i plug it into the computer.

---

### Post by MG&amp;TL on 2011-09-19
Nope, looks like your BIOS does not support USB.

Use a CD and *infrarecorder*.

Then load the cd, reboot and select CD in the BIOS. And away you go.

[http://infrarecorder.org/]("http://infrarecorder.org/")

---

### Post by derelict_space on 2011-09-19
alright, i don't have a cd to burn at the moment, but i'll ask a few friends and if that doesn't work out i'll pick up some cds and report back. thanks a ton for all the help, i'll make sure all your help doesn't go to waste.

---

