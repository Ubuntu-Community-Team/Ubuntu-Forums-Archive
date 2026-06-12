---
title: "Computer Restarts after &quot;Install Ubuntu&quot;"
date: 2010-03-08
forum: General Help
---

### Post by Munnzy on 2010-03-08
Hello everyone. Basically, I'm trying to reinstall ubuntu, but when I boot from the disc at start up and click "Install Ubuntu", my computer restarts. I've already burned a new CD thinking it was a problem with the other CD, but the problem still occurs. Any ideas on how to fix this? thanks for any help.

---

### Post by rogue_0111 on 2010-03-08
It may be a hardware issue. Try running from the CD. If it boots up fine try the install from the Desktop.

---

### Post by Munnzy on 2010-03-08
> **rogue_0111 said:**
> It may be a hardware issue. Try running from the CD. If it boots up fine try the install from the Desktop.

It restarts when I try to run it from the CD as well. Any other suggestions? 

Also, I've installed it before on my current setup and it worked fine and there haven't been any hardware changes.

---

### Post by patchwork on 2010-03-08
Did you check the md5sum to make sure the disk downloaded and burned correctly?

Is this the standard desktop disk or the minimal?   Have you tried using the command-line install and adding the desktop afterwards?

---

### Post by Villiam on 2010-03-08
My friend why don't you install it al fresh. I mean why to install on a preexisting system. Install it on a clean hard disk and I hope it will sail like anything.

---

### Post by Munnzy on 2010-03-08
> **patchwork said:**
> Did you check the md5sum to make sure the disk downloaded and burned correctly?

Is this the standard desktop disk or the minimal?   Have you tried using the command-line install and adding the desktop afterwards?

I'm using a standard desktop disk. I've tried multiple disks so I'm assuming the disc isn't the problem, but how do I check the md5sum to see if it is?

And I'm not sure how to install it with command-line but if it isn't too difficult I can try it out.

---

### Post by Munnzy on 2010-03-08
> **Villiam said:**
> My friend why don't you install it al fresh. I mean why to install on a preexisting system. Install it on a clean hard disk and I hope it will sail like anything.

I still need windows 7 for some things, so that isn't an option.

---

### Post by patchwork on 2010-03-08
There should be an option on the cd menu to check disk for defects.

The command line install is easy to do (it doesn't install FROM the command line, rather it only installs the system up-to the command line.   You will have to use apt-get to install ubuntu-desktop after the installation).   If the cd is ok, and it is the x server causing trouble, this can be troubleshot(?) after getting the heart of the system up and running.

---

### Post by Munnzy on 2010-03-08
> **patchwork said:**
> There should be an option on the cd menu to check disk for defects.

The command line install is easy to do (it doesn't install FROM the command line, rather it only installs the system up-to the command line.   You will have to use apt-get to install ubuntu-desktop after the installation).   If the cd is ok, and it is the x server causing trouble, this can be troubleshot(?) after getting the heart of the system up and running.

My computer restarts after pressing check disk for defects also.

---

### Post by patchwork on 2010-03-08
Wow, ok, not sure where else to go with this...

---

### Post by ciscosurfer on 2010-03-09
Munnzy,

md5sum information can be found on [this wiki page]("https://help.ubuntu.com/community/HowToMD5SUM").

Have you experienced any trouble like this (using discs) when using Windows 7? If so, you most likely have faulty hardware somewhere.

I would try burning a new ISO from another machine. If after verifying the integrity of the burn you still experience these issues, then you can likely rule out a bad burn and consider your hardware to be at fault.

Sometimes reboots will occur due to over heating. Is this a laptop or a desktop? How old? What make/model?

Could your power supply be damaged? A sudden surge can trigger a reboot/shutdown as well.

It's possible you have a dying PSU, CD/DVD drive, or motherboard.

---

### Post by rogue_0111 on 2010-03-09
Sounds like hardware.

---

