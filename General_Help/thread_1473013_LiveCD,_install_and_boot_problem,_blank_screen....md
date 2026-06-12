---
title: "LiveCD, install and boot problem, blank screen..."
date: 2010-05-04
forum: General Help
---

### Post by mkrmec on 2010-05-04
Hello all

Need help with my wierd situation. I installed a new graphic card from ATI 5770 (Club3D). After I did it I
removed the propriatery ATI drivers I had installed thru the "Hardware Drivers" in Ubuntu and rebooted.

Then I couldn't get into ubuntu again. When it starts booting the display just shuts down and says
"Power Saving mode". The computer continues to load things etc. left it running and hoped it would show
itself... :D nothing.

Anyway this happens everytime even with Live CD so I can't even get to a terminal...

Started the boot without the splash and it went blank after it started some Speech thing. Just before that there were a few firmware files missing.

Anyway I need the help, please have some good news for me.

---

### Post by mkrmec on 2010-05-07
Ok I've tried the Alternate version of 10.04. Installed ok, but the same problem came again. When it starts up the graphic drivers the display goes "Power Saving mode".

I've tried some sudo hacking and removed both drivers the open source ones and the ATI ones.

I was able to get into Ubuntu after this but now I can't do anything with drivers. the ATI ones don't work properly anyway. And the "Hardware" button is missing in the settings.

Man I really don't know why Ubuntu doesn't like my graphic card or whatever.

I had a 4770 before and when I changed to 5770, and from dual core to quad core Intel CPU nothing works anymore. Tried reinstalling same thing with the monitor shutting down.

Need help.. can't stand windows anymore..

---

### Post by mkrmec on 2010-05-09
Serioulsy? Nobody's got nothing to advise me?

There has to be some wierd thing to why I can't install it properly. Is it the drivers that come with the CD? They don't support ATI 5770 chips? I don't see any other problem. Want me to print out some things or whatever?

Please help!

---

### Post by Odox00 on 2010-05-09
Same here, but I have nvidia 6150. I just started out with Linux so I thought Ubuntu would be a neat start. 9.10 worked fine but upgrade to 10.04 the problem started.

---

### Post by Frogs Hair on 2010-05-09
> **mkrmec said:**
> Ok I've tried the Alternate version of 10.04. Installed ok, but the same problem came again. When it starts up the graphic drivers the display goes "Power Saving mode".

I've tried some sudo hacking and removed both drivers the open source ones and the ATI ones.

I was able to get into Ubuntu after this but now I can't do anything with drivers. the ATI ones don't work properly anyway. And the "Hardware" button is missing in the settings.

Man I really don't know why Ubuntu doesn't like my graphic card or whatever.

I had a 4770 before and when I changed to 5770, and from dual core to quad core Intel CPU nothing works anymore. Tried reinstalling same thing with the monitor shutting down.

Need help.. can't stand windows anymore..

See if the hardware and driver jockey is installed , you may have removed it . If not,  install it and click on it and it will search for drivers from the repository.

---

### Post by GSF1200S on 2010-05-09
Try my first post on the following thread:

[http://ubuntuforums.org/showthread.php?t=1466337](http://ubuntuforums.org/showthread.php?t=1466337)

To the OP: you will need to find the ATI equivalent of 'nomodeset' (which works for nvidia cards like mine) for my first post to be successful. I dont have an ATI card and I dont have much experience with them, so I cant be of much help :(

---

### Post by mkrmec on 2010-05-10
> **Frogs Hair said:**
> See if the hardware and driver jockey is installed , you may have removed it . If not,  install it and click on it and it will search for drivers from the repository.

Hardware thing is back in the administration section, and now I see the graphic card that I couldn't before.
BUT when I try to install it it gives me a nice error message: System error: install archives() failed

What if reinstalled via Desktop or Alternate and enter ubuntu in low graphics mode is that posible? And then install the driver.

---

### Post by mkrmec on 2010-05-10
just tried installing it though

jockey-text

commands I found on forums and it gave out the same error

```
Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).
```

---

### Post by mkrmec on 2010-05-10
I reinstalled the Alternative version of 10.04
when grub started I selected failsafe mode
then I started in failsafe mode or low graphic mode
ubuntu booted under low resolution and some other graphic drivers that work
went to System Administration Hardware and installed the propriatery drivers
restarted and it works :D

---

