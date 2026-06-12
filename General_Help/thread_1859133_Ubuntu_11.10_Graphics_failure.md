---
title: "Ubuntu 11.10 Graphics failure"
date: 2011-10-13
forum: General Help
---

### Post by silkworm2.5 on 2011-10-13
Hi all.
I tried installing Ubuntu 11.10 on my computer today. The live USB worked fine, logging in, unity ran smoothly, and it all looked good.
After installation however, The graphics simply don't work. Where LightDM is meant to display, all I get is a purple screen with black lines along it. Plymouth fails to display anything also, and on one random occasion where it managed to display the GUI, it was split down my monitor, starting the display near the middle and carrying on off screen.
I tried to log in and it froze.
I can access the TTY terminals and log in. but otherwise I am stuck.

Can anyone help me please?

Relevant Hardware: ATI Radeon Saphire 6750 2GB. Dual core 2.6 GHz CPU.

---

### Post by effenberg0x0 on 2011-10-13
Hey, try to follow the procedures I described in this thread, post #5 and on:

[http://ubuntuforums.org/showthread.php?t=1857059](http://ubuntuforums.org/showthread.php?t=1857059)

Regards,
Effenberg

---

### Post by silkworm2.5 on 2011-10-13
Thanks for replying.
I tried all of what you said but when executing the driver.run package, it says
```
package dpkg-dev has no installation candidate.
Unable to install dpkg-dev. Please install manually.
Package build failed!
```Without an Internet connection on Ubuntu yet, I can't use apt-get to install this either. Is there a place I can download it from and install it manually with its dependencies?

---

### Post by kipsiokas on 2011-10-13
The same thing with nividia GForce 555m.

---

### Post by effenberg0x0 on 2011-10-13
Kipsiokas: Instructions for Nvidia on post #27.
[http://ubuntuforums.org/showthread.php?p=11293922#post11293922](http://ubuntuforums.org/showthread.php?p=11293922#post11293922)

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-13
Silkworm: Instructions on how to install packages with no Internet connection:
[https://help.ubuntu.com/10.04/add-applications/C/offline.html](https://help.ubuntu.com/10.04/add-applications/C/offline.html)

Regards,
EFfenberg

---

### Post by silkworm2.5 on 2011-10-13
Ok, I managed to get the sources open and edit them in nano, mounted the USB drive I installed from on /media/cdrom and then ran sudo apt-get install dpkg-dev and it tells me that there are unmet dependencies. I checked and made sure I enabled the right source line (Not i386 and not Natty).
Is there anything else I can do?

---

### Post by silkworm2.5 on 2011-10-13
Whilst tinkering, I also found the command "apt-cdrom" and ran that, it detected the usb drive as a cdrom and got some kind of key from it. However, I still get an unmet dependencies error on attempting to install dpkg-dev.
Any more advice please?

---

### Post by effenberg0x0 on 2011-10-13
Great, when you ran apt-cdrom you have added the USB/CD-ROM unit to your /etc/apt/sources.list. It will be seqarched for the packages you need.

Now try to reinstall dpkg and fix broken dependencies.

The command would be sudo apt-get install --reinstall -f dpkg* 

Things would be incredibly easier if you have a network connection. 

Regards,
Effenberg

---

### Post by silkworm2.5 on 2011-10-13
Agh, this is doing my head in. apt-cdrom keeps telling me that there are no valid entries on the disc, so now I removed the graphics card, booted using the on board VGA port, and now I'm gonna get the wireless card working. If only the included drivers worked...
I'll be back after I get the card working and connected and dpkg-dev installed and can make some headway. Thanks for all your help!

---

### Post by 23dornot23d on 2011-10-13
Possibly needs the alternate CD or download the DVD .....

We were discussing recovery this way the other day in a thread .......

Link to thread .... [http://ubuntuforums.org/showthread.php?t=1858549](http://ubuntuforums.org/showthread.php?t=1858549)

---

