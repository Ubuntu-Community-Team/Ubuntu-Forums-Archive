---
title: "HELP? completely reformat my old computer"
date: 2010-07-16
forum: General Help
---

### Post by itsjoshgrant on 2010-07-16
ok i just found an OLD computer
and it works! but, it had no os on it so i instaled ubuntu 10.04 on it. but it is so slow... so i decided to install ubuntu mini on it instead. but i dont have an option to boot from cd when i boot up. so i enter my setup by pressing delete and it has a password that i do not know... is there some way IN ubuntu to wipe the hard drive or is there a way to get passed it?


any help would GREATLY be appreciated
THANKS!

---

### Post by Samulus on 2010-07-16
By ubuntu mini, do you mean the alternative cd installer? This version of ubuntu is the same once you've installed it as the normal version, If you don't have any important data on the hd and you still want to reformat I suggest that you go with either Lubuntu or the Linux Mint 9 LXDE RC. These both use LXDE instead of Gnome which are faster desktop enviorments for older computers. I personally recommend Linux Mint 9 LXDE RC as it's easy to use and great. I haven't tried Lubuntu though.

---

### Post by itsjoshgrant on 2010-07-16
> **Samulus said:**
> By ubuntu mini, do you mean the alternative cd installer? This version of ubuntu is the same once you've installed it as the normal version, If you don't have any important data on the hd and you still want to reformat I suggest that you go with either Lubuntu or the Linux Mint 9 LXDE RC. These both use LXDE instead of Gnome which are faster desktop enviorments for older computers. I personally recommend Linux Mint 9 LXDE RC as it's easy to use and great. I haven't tried Lubuntu though.

ok ill do that
but... i dont know how to refomat my computer -_-

---

### Post by HenneBaby02 on 2010-07-16
> **itsjoshgrant said:**
> ok ill do that
but... i dont know how to refomat my computer -_-
reformatting the hard drive is easy, installing a Operating system will delete and format your computer for you :)

---

### Post by SnickerSnack on 2010-07-16
> **itsjoshgrant said:**
> ok ill do that
but... i dont know how to refomat my computer -_-

The installer will do that.

edit: ninjad

---

### Post by itsjoshgrant on 2010-07-16
> **SnickerSnack said:**
> The installer will do that.

edit: ninjad

yeah but im saying since i instaled ubuntu its not booting directly from cd and i pressed delete to enter startup but it has a password on it... is there another way besides booting a cd to clean the hard drive?

---

### Post by TechBeastie on 2010-07-16
Ah - so you're pressing Delete to try to get the computer to boot from something other than the hard drive?  If that's the case, the problem here isn't with the hard drive, but with your system's BIOS, which apparently has a admin password installed.  If this computer is a desktop, there's a fairly easy way to clear the password:  All you have to do is open up the case and short out the password-reset "jumper" on your motherboard (What you're looking for, basically, is a set of 3 small metal pins sticking about half-an inch up from the surface of the Motherboard, 2 of which will be bridged by a small plastic block.  These pins will usually be located near the clock battery).  I realize these instructions are a bit vague, but many others have written BIOS-password-reset tutorials, and if you google "reset bios password," you should find what you need.  

Good luck!

---

### Post by renkinjutsu on 2010-07-16
If you don't think shorting your mobo is the way to go, then i guess one way to do this is to take out all the drives and boot from your CD/USB so that the bios goes through the complete list of boot devices without ever reaching the harddrive.. This way, you don't have to manually select a boot device which would require a password.


Now the problem would be to hotplug the harddrive while the system is booted ;)

.. wait. How did you install Ubuntu on it to try it out if you can't even boot into a CD?

---

### Post by SnickerSnack on 2010-07-16
> **renkinjutsu said:**
> If you don't think shorting your mobo is the way to go,

That jumper is designed for that purpose.  It's the only way to reset the password (afaik).

> **renkinjutsu said:**
> .. wait. How did you install Ubuntu on it to try it out if you can't even boot into a CD?

Good question.....

---

### Post by itsjoshgrant on 2010-07-16
> **renkinjutsu said:**
> If you don't think shorting your mobo is the way to go, then i guess one way to do this is to take out all the drives and boot from your CD/USB so that the bios goes through the complete list of boot devices without ever reaching the harddrive.. This way, you don't have to manually select a boot device which would require a password.


Now the problem would be to hotplug the harddrive while the system is booted ;)

.. wait. How did you install Ubuntu on it to try it out if you can't even boot into a CD?

idk ... at first it had no OS on it so i guess it was defaultly set to run a cd then when i installed ubuntu i started booiting from the hard drive so...

---

### Post by SnickerSnack on 2010-07-16
double post?

---

### Post by SnickerSnack on 2010-07-16
> **itsjoshgrant said:**
> idk ... at first it had no OS on it so i guess it was defaultly set to run a cd then when i installed ubuntu i started booiting from the hard drive so...

I'd guess that the current boot order has HD before CD, so when there was no OS (and the HD was not bootable), it was possible to boot from the CD.

It *may* be possible to remove the boot flag from the HD while in ubuntu.  Though, it may take some jumping through hoops to do it.

I also agree that removing the HD during boot and then reconnecting it after boot would work, at least for now.

Resetting the password manually is probably the best option, though.  The other options are work-arounds that don't solve the cause of the problem, so you'll have the same problem if you ever want to boot from the cd (or usb) again.

Edit: Have you tried booting from USB?  (ubuntu has a USB startup disk creator)

---

### Post by renkinjutsu on 2010-07-16
I like the idea of booting into Ubuntu and messing up the install..

Boot into it and do something like: ```
sudo dd if=/dev/zero of=/dev/sda bs=1024 count=1
```
I think the 512 should be alright, but i don't really remember.. 1024 just to be safe.. I think that renders the drive unbootable.. right? Or is the bootflag still there even after messing up the mbr?

---

