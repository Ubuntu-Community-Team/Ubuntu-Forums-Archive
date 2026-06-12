---
title: "Unetbootin hard drive install failed."
date: 2010-09-01
forum: General Help
---

### Post by Austin25 on 2010-09-01
I have Xubuntu installed on my Desktop, and I want to dual boot Ubuntu Server Edition. The computer is old, so I need to boot the CD from [here]("https://help.ubuntu.com/community/BootFromUSB") to boot from a USB drive.(I know that the iso isn't the problem, for I have used it before.) I can't burn CDs, due to the problem [here]("http://ubuntuforums.org/showthread.php?t=1549953"), so I need to use the unetbootin temporary hard drive install. Instead of showing a menu to boot from the USB drive, It booted directly into Xubuntu. Can anyone help?

---

### Post by dtfinch on 2010-09-01
Did you make sure the usb drive was above your hard drive in the boot order in your bios? Alternatively, many let you press a key (usually F11 I think) to select the which device to boot.

Something else to watch out for (not the problem you're having now) is that unetbootlin seems to have trouble copying the server/alternative cd correctly to usb, due to this: [https://bugs.launchpad.net/unetbootin/+bug/373089](https://bugs.launchpad.net/unetbootin/+bug/373089)
I gave up and used the cd for Lucid server installs.

A third option I've tried is installing within virtualbox, then migrating it to the partition, but that presented other difficulties, like vboxmanage -clonehd having an undisablable feature where it changes the partition uuids, but there's ways to fix it, and other ways to copy it.

---

### Post by Austin25 on 2010-09-01
> **dtfinch said:**
> Did you make sure the usb drive was above your hard drive in the boot order in your bios? Alternatively, many let you press a key (usually F11 I think) to select the which device to boot.

Something else to watch out for (not the problem you're having now) is that unetbootlin seems to have trouble copying the server/alternative cd correctly to usb, due to this: [https://bugs.launchpad.net/unetbootin/+bug/373089](https://bugs.launchpad.net/unetbootin/+bug/373089)
I gave up and used the cd for Lucid server installs.

A third option I've tried is installing within virtualbox, then migrating it to the partition, but that presented other difficulties, like vboxmanage -clonehd having an undisablable feature where it changes the partition uuids, but there's ways to fix it, and other ways to copy it.
The usb drive is not enabled in the bios, that's why I need to boot the chainloader CD.
It hasn't gotten to the point where it tries to boot from the USB drive yet.
Maybe I could try migrating from Virtual box, but it would be useful to boot that chainlader CD using unetbootin.

---

### Post by Austin25 on 2010-09-02
Bump.

---

### Post by dtfinch on 2010-09-02
For creating the bootable usb installer, there's also a usb-creator-gtk package that I haven't tried. I don't think it has the same long filename problem with alternative/server installs as unetbootin.

Or it looks like there's a way to skip the use of removable media altogether:
[https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD](https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD)
The instructions assume you want to install to /dev/sda1, which you'll almost certainly want to change. And you'll want to substitute the ubuntu-server package for ubuntu-desktop in the last step.

---

### Post by wojox on 2010-09-02
Just press Ctrl+Alt+F1

Login in and bingo, welcome to server mode.

---

### Post by Austin25 on 2010-09-03
> **dtfinch said:**
> For creating the bootable usb installer, there's also a usb-creator-gtk package that I haven't tried. I don't think it has the same long filename problem with alternative/server installs as unetbootin.

Or it looks like there's a way to skip the use of removable media altogether:
[https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD](https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD)
The instructions assume you want to install to /dev/sda1, which you'll almost certainly want to change. And you'll want to substitute the ubuntu-server package for ubuntu-desktop in the last step.
The problem isn't the creating a bootable flash drive, unetbootin is working for that on another computer, although unetbootin for the temporary hard drive install isn't working. See [here]("http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes") for the difference.

---

### Post by Austin25 on 2010-09-03
> **wojox said:**
> Just press Ctrl+Alt+F1

Login in and bingo, welcome to server mode.
Then I still have the overhead of the gui though.

---

### Post by Austin25 on 2010-09-03
> **dtfinch said:**
> A third option I've tried is installing within virtualbox, then migrating it to the partition, but that presented other difficulties, like vboxmanage -clonehd having an undisablable feature where it changes the partition uuids, but there's ways to fix it, and other ways to copy it.
How would you suggest I do this?

---

### Post by Austin25 on 2010-09-03
bump.

---

### Post by Austin25 on 2010-09-03
Well, I tested the hard drive install feature on my laptop with a different is, and it did the same thing, so I think I found a bug with unetbootin.

---

### Post by Austin25 on 2010-09-04
Figured it out, I needed to hold shift as it was booting up to enter the grub menu.

Thanks for the help.

---

