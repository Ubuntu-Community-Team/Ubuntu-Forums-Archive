---
title: "Newbie black screen when loading Ubuntu"
date: 2011-03-10
forum: General Help
---

### Post by nozborne on 2011-03-10
My son's mother picked up an old Panasonic Toughbook CF-18 from her employer when they upgraded to new hardware.  Based on the info I got from her, it came loaded with Ubuntu.  She was doing an upgdate and either the battery died in the laptop mid-stream or the update somehow failed.

The last screen I get is one which says "Ubuntu" and has a status bar of several white dots which turn red.  Once they are all red, the screen goes to black.  There are no sounds or anything like that.

By pressing ESC I get to a menu which has several different kernels listed and each with a (recovery mode) option.  I am able to load up with another one of the kernels.  When I restart, I get the black screen again and have to manually go through the process to choose the kernel each time.  Is there a way to change the default kernel or easily "fix" the one that isn't loading?

Thanks for reading.

---

### Post by ikt on 2011-03-10
> **nozborne said:**
> My son's mother picked up an old Panasonic Toughbook CF-18 from her employer when they upgraded to new hardware.  Based on the info I got from her, it came loaded with Ubuntu.  She was doing an upgdate and either the battery died in the laptop mid-stream or the update somehow failed.

The last screen I get is one which says "Ubuntu" and has a status bar of several white dots which turn red.  Once they are all red, the screen goes to black.  There are no sounds or anything like that.

By pressing ESC I get to a menu which has several different kernels listed and each with a (recovery mode) option.  I am able to load up with another one of the kernels.  When I restart, I get the black screen again and have to manually go through the process to choose the kernel each time.  Is there a way to change the default kernel or easily "fix" the one that isn't loading?

Thanks for reading.

While you are in the recovery mode with networking of the last kernel that worked, are you able to do:

sudo apt-get update

and then

sudo apt-get upgrade

and see if it has anything to install/upgrade or fix?

---

### Post by prshah on 2011-03-10
> **nozborne said:**
> My son's mother

She was doing an upgdate and either the battery died in the laptop mid-stream or the update somehow failed.

easily "fix" the one that isn't loading?


Irrelevant question: Your "son's mother"; wouldn't that be your wife? 

To fix an interrupted upgrade, please see [the first post in this thread]("http://ubuntuforums.org/showthread.php?t=780531") for a solution and gotchas.

---

### Post by nozborne on 2011-03-10
prsha - Not in this situation :)

ikt - I see a whole bunch of "W: Failed to fetch...Something wicked happened resolving..."  I am guessing I need to put it on a wired network or is there a way to do this on wireless?

---

### Post by Hedgehog1 on 2011-03-10
> **nozborne said:**
> ... was doing an upgdate and either the battery died in the laptop mid-stream or the update somehow failed.

nozborne,

May I suggest that rather than try to 'save' the partial install on this system, you instead download the Ubuntu ISO, burn it to a CD and do a clean install?

This will give your son the cleanest possible PC with things installed at a 'known state'.

[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Less pain all around, I should think.

***The Hedge***

:KS

---

### Post by nozborne on 2011-03-10
Hedgehog1, I wish I could.  Unfortunately I don't have a CD-ROM for this laptop.  It is a Toughbook which is a few years old and does not have any optical drives.  If there is a way to do this via USB I am certainly open, but I didn't see any setting in the Bios that would allow me to choose to boot from USB.  Again, this could be my ignorance so I am open to any suggestions.

---

### Post by Hedgehog1 on 2011-03-10
You, good sir, are in luck!

You can indeed install off a USB.

[http://www.pendrivelinux.com/category/new-usb-linux-tutorials/]("http://www.pendrivelinux.com/category/new-usb-linux-tutorials/")

or

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

You can take a downloaded iso and use the tool from the above link to create a 'LiveUSB'; no CD needed at all.

***The Hedge***

:KS

p.s. making bootable USB sticks is a hobby unto itself, too. great fun!

---

### Post by prshah on 2011-03-11
> **nozborne said:**
> If there is a way to do this via USB I am certainly open, 

Before you re-install, can you try the ```
dpkg --configure -a
``` command from a recovery root terminal (as suggested in the linked thread in my previous post?)

It certainly won't make things any worse, and may help. Please post back errors if you encounter any.

---

### Post by ikt on 2011-03-11
> **nozborne said:**
> prsha - Not in this situation :)

ikt - I see a whole bunch of "W: Failed to fetch...Something wicked happened resolving..."  I am guessing I need to put it on a wired network or is there a way to do this on wireless?

I would say a wired network would be quicker and easier.

> **prshah said:**
> Before you re-install, can you try the ```
dpkg --configure -a
``` command from a recovery root terminal (as suggested in the linked thread in my previous post?)

It certainly won't make things any worse, and may help. Please post back errors if you encounter any.

The above is actually what I intended to do, just couldn't remember the name of the command, since afaik apt-get upgrade will try to finish off any not finished installations anyway, dpkg --configure -a will just do it without needing to be on a network, so I definitely recommend trying the above and seeing if it works.

---

### Post by prshah on 2011-03-13
> **ikt said:**
> afaik apt-get upgrade will try to finish off any not finished installations anyway, dpkg --configure -a will just do it without needing to be on a network

apt-get will NOT finish unfinished or interrupted installations. If the installation is in an error state, apt-get will simply fail with errors.

the dpkg configure command, with -a (all) will finish unfinished / interrupted installations.

When an apt-get upgrade is performed, all required packages are fetched first, before the installation starts. So if the installation (not downloading) is interrupted, then dpkg will not need a network connection to finish the interrupted installation / upgrade.

If the downloads were not completed, then dpkg will not do anything (since there is nothing to do as the installation would not have started at all).

---

### Post by nozborne on 2011-03-18
So I tried the dpkg command and still no love...
I have created a bootable usb for 10.10 per the instructions on the link above but it still seems to load from the HDD instead of this USB drive, flash the splash screen and then go to the blank screen.

I can boot in recovery mode to the command line and I can boot the GUI for previous kernels.  Is there any way to load the new OS from one of those interfaces or any ideas how to get it to just boot from this USB drive?  

Thanks all.

---

### Post by nozborne on 2011-03-20
Anybody?  Please.

---

### Post by Hedgehog1 on 2011-03-20
Hello Again!

To boot from the USB, you will need to tell the tough book's bios to change boot order.

When you boot and see the first logo & text, there is typically some instructions to get into the bios.

The keys can be F1, F10, F11, [DEL] - every manufacturer is different (just to annoy us).

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-20
In case you need it, here is a link to the manual for that laptop:

[toughbook_cf_18_manual]("http://www.fixya.com/support/p375295-panasonic_toughbook_cf_18_tablet_pc/manual-8392")

Page 38 talks about using F2.

EDIT: Here is the **SERVICE** manual as a PDF: [CF-18JHU70TW.pdf]("http://tim.id.au/laptops/panasonic/CF-18JHU70TW.pdf"). This has the good details - even what the beeps at POST mean!

***The Hedge***

:KS

---

### Post by nozborne on 2011-03-20
Thanks Hedgehog, but part of the prob is that USB is not one of my boot options in the bios.  I am hoping to be able to somehow do it from a command line or the gui using a previous kernel that works.

---

### Post by Krytarik on 2011-03-20
I may jump in here, as I'm following this thread. How about this?:
- check if there a "/boot/grub/grub.cfg" on the USB drive, should be
- if so, copy the respective menu entry into your "/etc/grub.d/40_custom"
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)
- check/update the device specifiers based on the output of
```
sudo blkid
```- update grub
```
 sudo update-grub
```
- if successful, choose at the boot menu the respective new option

---

