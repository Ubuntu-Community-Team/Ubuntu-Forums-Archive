---
title: "Wubi not working for Asus computer"
date: 2011-11-07
forum: General Help
---

### Post by leshurv on 2011-11-07
Hey all!
 
I just purchased an Asus N55S computer the other day with Intel i7, and I've been trying to install Ubuntu via Wubi so that I can use Ubuntui through Windows 7, but it's not working. I'm brand new to all of this, so any help would be greatly appreciated!
 
 
Wubi downloads fine, and it re-starts, but when my computer starts booting back up again, it seems to get stuck in the re-boot at the following:
 
[44.890193] lp: driver loaded but no devices found
[44.904469] ppdev: user-space parallel port driver
[45.338218] type=1400 audit (1320714203.132:11): aparmor="STATUS" operation="profile-load" name="usr/lib/cups/backend/cups-pdf" pid=6977 comm="apparmor_parser"
[45.339688] type=1400 audit (1320714203.136:12)" apparmor="STATUS" operation= "profile_load" name="/usr/sbin/cupsd" pid=6977 comm="aparmor_parser"
 
 
Once it gets stuck at this point, I end up just shutting down my computer and re-starting it. When I re-start it, Ubuntu comes up as an option, but when I choose Ubuntu, it comes to a pink screen for about a minute and then the screen just goes black. So, I then restart my computer again, and just load Windows 7. When I go into my Programs in Windows, Ubuntu is listed, and I'm able to delete i as a program, so it seems like it's halfway loaded, but not quite there I guess.
 
Thanks for the help!

---

### Post by bluexrider on 2011-11-07
This may help

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by leshurv on 2011-11-07
ah yea I saw that - I tried installing 11.04 via Wubi, but that didn't work, either. Thanks for the help, though!

---

### Post by leshurv on 2011-11-08
Could it possibly be because Ubuntu doesn't support Intel 64-bit PCs yet? I was looking at alternative downloads, and noticed that there were downloads for AMD 64-bit and Intel x86. I'd appreciate any help!

---

### Post by pavi_elex on 2011-11-08
Did the ubuntu install successfully and only problem is in booting ubuntu?
or it is not going to install with wubi?

---

### Post by Mark Phelps on 2011-11-08
My guess, from the error messages, is that it thinks you have a printer connected through a parallel port and is failing in the attempt to load a driver for it.

If you DO have such a printer, disconnect it and THEN retry installing via Wubi.  See if that makes a difference.

---

### Post by leshurv on 2011-11-08
> **pavi_elex said:**
> Did the ubuntu install successfully and only problem is in booting ubuntu?
or it is not going to install with wubi?


Wubi installed successfully, but when I go to re-start my computer and boot it, that's where the problem lies. It doesn't want to go through the whole booting process.

---

### Post by leshurv on 2011-11-08
> **Mark Phelps said:**
> My guess, from the error messages, is that it thinks you have a printer connected through a parallel port and is failing in the attempt to load a driver for it.

If you DO have such a printer, disconnect it and THEN retry installing via Wubi.  See if that makes a difference.


I do not have a printer, so it shouldn't be trying to connect to that. I literally just got the computer a couple of days ago, and I've been trying to install Wubi/Ubuntu before I put anything new/extra on my computer. So, I haven't installed any external devices, and I haven't added any new software yet at all. Is there anything else that it could be trying to connect to?

---

### Post by bcbc on 2011-11-08
The problem is due to your graphics card. Try booting with the 'nomodeset' option: [http://ubuntuforums.org/showthread.php?t=1613132http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132http://ubuntuforums.org/showthread.php?t=1613132)

For wubi first boot see post #8.

---

### Post by leshurv on 2011-11-08
> **bcbc said:**
> The problem is due to your graphics card. Try booting with the 'nomodeset' option: [http://ubuntuforums.org/showthread.php?t=1613132http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132http://ubuntuforums.org/showthread.php?t=1613132)
 
For wubi first boot see post #8.
 
 
 
Thanks for the help! It was really close to working, but still a no go :(. It goes through the whole installing process, and then I can pick between Ubuntu normal and Ubunto Recovery Mode. I chose the normal Ubuntu, it loads for a minute, and then the screen just goes black. Any idea what I could be doing wrong? :confused:

---

### Post by bcbc on 2011-11-08
> **leshurv said:**
> Thanks for the help! It was really close to working, but still a no go :(. It goes through the whole installing process, and then I can pick between Ubuntu normal and Ubunto Recovery Mode. I chose the normal Ubuntu, it loads for a minute, and then the screen just goes black. Any idea what I could be doing wrong? :confused:

Yes. That override is a one-time thing. Go back to that same thread for instructions on how to override again - this time follow the instructions on post #1 (ignore where it says 'not for wubi' as it's the same after the initial install).

after that you'll need to go to 'additional drivers' to get your graphics working normally.

---

