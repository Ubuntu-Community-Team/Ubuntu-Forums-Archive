---
title: "Video Card Issue - Desktop Effect not working, etc.."
date: 2010-02-24
forum: General Help
---

### Post by Xora on 2010-02-24
Hello, all so heres the issue or issues. 
1. When I try to enable Desktop Effects it says "Searching for Available Drivers" then says "Desktop effect could not be enabled".
2. When I play and game the has 3d Modeling, it chops to about 3 FPS and is completely unusable. 

But heres the deal, I have a ATI Raedon X850XT Platinum card, which I know can handle it. 
I'm using Ubuntu 9.10 and have everything up to date.
Help very appreciated.

---

### Post by 3rdalbum on 2010-02-24
The X850XT is not on ATI's supported list anymore. If you can't enable Compiz, then the open-source driver for your card does not support 3D.

I suggest upgrading your card to something that ATI or Nvidia supports, then you can get 3D acceleration.

---

### Post by Xora on 2010-02-24
Not sure how to do that, any suggestions?

---

### Post by Xora on 2010-02-25
I mean I know I how to upgrade the card, but I don't have another. Isn't there another driver option?

---

### Post by 2hot6ft2 on 2010-02-25
Found a driver for it for linux here:
[Driver Ati Radeon Catalyst Linux x86 8.7]("http://en.kioskea.net/telecharger/telecharger-850-driver-ati-radeon-catalyst-linux-x86")

Not sure if it's going to work or not but a quick search found it with the very first link
[linux ATI Raedon X850XT Platinum search]("http://www.google.com/search?q=linux+ATI+Raedon+X850XT+Platinum&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

---

### Post by gradinaruvasile on 2010-02-25
Not really. Unless you find some PPA's with updated drivers...

Open a terminal and type:

glxinfo | grep "direct rendering"

if the direct rendering (3d rendering) is enabled you should see:

direct rendering: Yes

Also you might try removing the /etc/X11/xorg.conf file if there is any:
In a terminal type:

sudo rm /etc/X11/xorg.conf
Reboot.

If you want working 3d features and stability, buy an nvidia card, those have the best driver support in Linux.


PS. That card of his isnt supported anymore by the Linux proprietary drivers. And the older drivers that support it work only with up to Ubuntu 8.10 - its Ati's decision, not Ubuntu's BTW. 
Dont install that driver, it will break your system.

---

### Post by 2hot6ft2 on 2010-02-25
Then there's this from here:
[http://www2.ati.com/drivers/linux/linux_8.14.13.html](http://www2.ati.com/drivers/linux/linux_8.14.13.html)
the 4th link in the search

> New ATI Proprietary Linux Driver Installer

The new ATI Proprietary Linux Driver Installer makes installing the ATI Linux driver a much simpler and user friendly experience. The installer provides for automatic and custom driver installations. Further, the ATI Proprietary Linux Driver Installer provides an option to generate distribution specific driver packages.
New ATI Hardware Product Support

This release of the ATI Proprietary Linux driver introduces support for the following ATI Products:

    * Radeon® X800 XL
    * Radeon® X850 PRO
    * Radeon® X850 XT
    * [B]Radeon® X850 XT Platinum Edition 
[/B]
Linux 2.6.11 Kernel Support

This release of the ATI Proprietary Linux driver introduces driver compatibly with Linux 2.6.11 kernel.
Minimum System Requirements

Before attempting to install the ATI Proprietary Linux driver, the following software must be installed:

    * POSIX Shared Memory (/dev/shm) support is required for 3D apps
    * glibc version 2.2 or 2.3
    * Linux kernel 2.4 or higher
    * XFree86 version 4.1, 4.2, 4.3, or X.org 6.8

			Note: 	If you are unsure of which version of XFree86/X.org is installed on your system, download and run check.sh from a command line to verify the version. 
They even have a phone number at the bottom of the page
>   ATI Technologies Inc.
[http://www.ati.com](http://www.ati.com)
Voice: (905) 882-2600
Fax: (905) 882-2620

---

### Post by gradinaruvasile on 2010-02-25
> **2hot6ft2 said:**
> XFree86 version 4.1, 4.2, 4.3, or X.org 6.8

That is the old X server version (6.8 ) (which was in Ubuntu 8.10 i believe). 

Ubuntu 9.10 has 7.4 or 7.5. That driver doesnt work anymore with this x server because of many changes in handling graphics. Only the newer crop of Ati's drivers work, but those dont support this card anymore.

---

### Post by 2hot6ft2 on 2010-02-25
> **gradinaruvasile said:**
> That is the old X server version (6.8 ) (which was in Ubuntu 8.10 i believe). 

Ubuntu 9.10 has 7.4 or 7.5. That driver doesnt work anymore with this x server because of many changes in handling graphics. Only the newer crop of Ati's drivers work, but those dont support this card anymore.
That's not good for the OP. Guess my searches wont be of any use then. I'm with you on the NVIDIA cards
> **gradinaruvasile said:**
> 
If you want working 3d features and stability, buy an nvidia card, those have the best driver support in Linux.
But that doesn't help the OP much. Mine are all NVIDIA.
I tried. Glad you were here to stop Xora from trying any of them.

---

### Post by Xora on 2010-02-25
Thanks everyone, I guess I'm kinda torn here. I run a dual boot and my windows side is upgraded using this card from games vs the original card however Ubuntu likes the other card. 

Oh well, I plan on updating cards soon. Any suggestion that would work well with both system for both high end gaming and 3d Design?

---

### Post by gradinaruvasile on 2010-02-26
Anything that works with games works with 3d design AFAIK.
I would suggest Nvidia - at least 220. I use a 210 and its not as fast as a 7600GS 3d performance wise. 
The 220 has fast 3d and supports VDPAU C set (all features) - meaning it kicks ***** in HD movie playing (i tested the 210 and i had 5% CPU load playing 1080p movies with the vdpau enabled mplayer).

---

### Post by 3rdalbum on 2010-02-26
Any current Nvidia card will work well. I have a GTX260 which handles anything I've thrown at it (including GRID in Wine).

---

