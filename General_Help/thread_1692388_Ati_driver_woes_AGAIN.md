---
title: "Ati driver woes AGAIN"
date: 2011-02-21
forum: General Help
---

### Post by ~Middle on 2011-02-21
So i have just install Ubuntu, and i am having some more issues with the ati drivers... 

I first installed the drivers that Ubuntu prompted me to use from Additional Drivers... however i then downloaded a newer version, so that i can run a program... now i just get a blank screen when i boot....

How can i remove all the drivers from the CLI? So then i can restart Ubuntu with no graphics driver installed (like on first time boot) and then just install the recommended drivers.

Ubuntu 10.10
Radeon 5870

Thanks a lot for your time!

EDIT: I can't even get into recovery mode it just has no output...

May have to do a clean install for the 4th time..

I am going to do a clean install, this is literally the 4th or 5th time i have done this in under a week... I hate Ati!

---

### Post by ~Middle on 2011-02-21
Oh hey....

So i installed, Ubuntu, updated it, rebooted, installed Catalyst, rebooted, configured Ubuntu:

Installed: 

dropbox *loads on startup*
conky *loads on startup*
irssi
pyrit (Includes):
- [http://orwell.fiit.stuba.sk/~nou/ati-opencl-runtime_2.1_amd64.deb](http://orwell.fiit.stuba.sk/~nou/ati-opencl-runtime_2.1_amd64.deb)
- [http://orwell.fiit.stuba.sk/~nou/ati-opencl-dev_2.1.deb](http://orwell.fiit.stuba.sk/~nou/ati-opencl-dev_2.1.deb)
- libssl-dev
- python-dev
- python2.6-dev
- zlib1g-dev
- libpcac0.8-dev
hamachi *loads on startup*

Set all my icons nice, got my wallpaper and terminals perfect etc...

Rebooted... black screen....

I have done this too many times, is anybody willing to SSH into my box,  and see if they can figure out what is wrong and fix it please!!

Ubuntu 10.10 installed an hour an hour ago with the above changes
Graphics card: Radeon HD 5870
Graphics driver: Catalyst 11.2

Thanks to anyone willing to help. I do expect some 'google it' replies, but i  have been googling it for the last 5 installs of Ubuntu... So some direct help  would be greatly appreciated!

EDIT: Yes i have tried adding nomodeset to the grub line, with no success. I am trying to add 'single' but i get the recovery menu.. unsure on this...

---

### Post by keithpeter on 2011-02-21
Hello ~Middle

When you boot, do you see the grub menu?

If so, do you have the recovery option?

Suggestion: if so, boot with recovery option, then apt-get remove things one by one until the situation improves.

PS: I've used dropbox on umpteen Ubuntu installs without issue

---

### Post by ~Middle on 2011-02-21
OK that is good to know!

<3 dropbox... makes re installations so much easier!

Yes, i suppose you are right with that... however there is one thing i am not sure of.

When i installed hamachi:

[https://secure.logmein.com/labs/logmein-hamachi_2.0.1.13-1_amd64.deb](https://secure.logmein.com/labs/logmein-hamachi_2.0.1.13-1_amd64.deb)

I had to do: sudo apt-get install -f

then that installed a lot of other packages....

EDIT: Because i couldn't isntall lsb for hamachi to work....

EDIT: _[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)_

Got me back into a GUI :0

---

### Post by keithpeter on 2011-02-21
> **~Middle said:**
> OK that is good to know!

When i installed hamachi:

[https://secure.logmein.com/labs/logmein-hamachi_2.0.1.13-1_amd64.deb](https://secure.logmein.com/labs/logmein-hamachi_2.0.1.13-1_amd64.deb)

I had to do: sudo apt-get install -f

then that installed a lot of other packages....



Did you save the terminal session? Do you know what packages got installed?

I have no experience of hamachi, others here may have

---

### Post by ~Middle on 2011-02-21
Yeah i think i have figured it out.

It is the Ati driver that causes the crash, however it is very hard to remove, i have only just found this:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

so i am going to now try to install the community driver... see what happens...

Thanks for your help

---

### Post by hdtvchris on 2011-02-22
same problem with Gigabyte Radeon HD 5450 1GB
when i install the driver from Additional Drivers i get a black screen and i cant boot the system in any way

only solution to re-install ubuntu

---

### Post by seawolf167 on 2011-02-22
After your install, do not install the drivers from System -> Preferences -> Hardware Drivers, instead, install ATI's graphics suite from here:

[Driver Suite]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

[Direct Download Link]("http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run")

[ATI Radeon HD 5450]("http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-5000/hd-5450-overview/pages/hd-5450-overview.aspx")

---

### Post by 77_Chris on 2011-03-12
Hej!

You don't have to reinstall Ubuntu if you get a black screen.

A simple way to get it working again is to use TTY1 (Ctrl+Alt+F1). Log in, go to /etc/X11 and use the backup of the xorg.conf file.

The backup is created automatically when you run aticonfig --initial and is called something like xorg.conf...old.

You only have to replace your current xorg.conf by the backup version, reboot and everything is fine again (Well, besides the fact that the Ati-driver is not working for you...;)).

Cheers!

---

