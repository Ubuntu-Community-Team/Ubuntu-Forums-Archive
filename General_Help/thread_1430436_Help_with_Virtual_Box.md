---
title: "Help with Virtual Box"
date: 2010-03-15
forum: General Help
---

### Post by haldavnekar on 2010-03-15
I am new to Ubuntu (Linux). I installed VirtualBox 3.1x on my Laptop (Dell M6400, Windows 7 Ultimate 64-bit, 2.53 Quad core, 8GB DDR3, 2x250 gb HDD Non Raid, NVIDIA 3700M Quadro FX, 1920x1200 WUXGA screen).

I installed Ubuntu 9.04 64-bit as one the two guest OSes (Win XP 32-bit for other). I am running into a few of problems for the Ubuntu.

I assigned all four cores, 1GB of Ram, and 128MB of V-Ram (max allowed on VBox) for Ubuntu.

First, the maximum resolution I am getting for the Ubuntu is 800x600.  Correspondingly Win XP can get the full 1600x1200 for the 4:3 aspect ratio.  How can I fix the problem.  I downloaded and installed NVIDIA drivers through PPA, still no avail.  The system starts with saying "Resolution very low - Start once at low resolution."  While I can live without getting the 1600x1200 resolution like the XP, 800x600 is too low. Also, is there any way to change the aspect ratio from 4:3 to use the native screen aspect ratio of 16:10?

Second, the Ubuntu does not seem to recognize the wireless card of the host. I tried many different options like NAT, creating network bridge, etc. Still nothing.

Finally, the USB drives are not detected by Ubuntu. Again I tried all different options to make sure I did not leave any stone unturned.

Any help would be highly appreciated.

---

### Post by andrewwardrobe on 2010-03-15
Have you tired installing the GuestAdditions? (Devices Menu -> Install Guest Additions) and run autorun.sh, That normally fixes issue both with screen sizing and with USB pass through.


Also are you using the Open Source Edition of the Virtual Box or the Non-OS version as the last time i checked the Open source edition didn't support USB (may have change by now), if you did not compile your virtual box from source your proabably using the non-open source version

---

### Post by howefield on 2010-03-15
> **haldavnekar said:**
> Finally, the USB drives are not detected by Ubuntu. Again I tried all different options to make sure I did not leave any stone unturned.

You need to download the PUEL version from the virtualbox.org website. This version contains some closed source code which you won't find in the repository edition and which give you additional features such as USB support.

You need to uninstall the current version (if it is the OSE version) and install the PUEL.

You won't lose your virtual machines during this procedure.

Virtualbox uses it's own drivers for your guests, hence the reason why your installing nvidia drivers into the guest made no difference. Installing guest additions will install an improved graphics driver which will allow you to resize the guest window up to full screen, there are other benefits such as non capture of the mouse.

---

### Post by mkvnmtr on 2010-03-15
As I understand your host is windows 7. Like others said install the guest additions on each guest. Also I would recomend you download the manual from the Sun site. It should have all the typs you need to get things running. Ubuntu runs great ina Virtual Box.

---

### Post by haldavnekar on 2010-03-15
Thanks for your reply.

I have downloaded the PUEL version of the software.

I will try the recommendations and see if I get problems. I can definitely see Ubuntu running great in VBox apart from the three issues I mentioned.

---

### Post by monicamaria on 2010-04-09
Here are the steps that worked for me:

On the desktop:
 Menu System > Administration > Users and Groups
Click the keys to make changes, type password
Highlight you, the user, then click Properties
Under the "User Privileges" tab, scroll down and check the "Use Virtual Box" 
Click OK, then close.

Hope this helps.

Monica

---

### Post by arma0012 on 2010-04-10
I have the Sun Virtualbox system, which I think is the PUEL version. I've enabled the 'Use Virtualbox' in User Privileges and installed the guest additions & is now letting me resize the window.

I still can't get usb connectivity though. Is there anything else, even anything seemingly obvious I may have forgotten that could effect this?

Also what should my usb settings in Virtualbox be?

Thanks in advance,

Sam

---

### Post by coldraven on 2010-04-10
Have you ticked the boxes in the devices section of VBox for USB?
In fullscreen mode if you move the mouse to the bottom middle of the screen a tab appears, on this  you can enable any device on the fly. Say for example you just plugged some USB device in during your virtual session it will appear on this tab.
It works for me having Ubuntu host with XP guest.

---

### Post by arma0012 on 2010-04-10
When I click on 'usb devices', I can see a list of the devices that are ticked in the virtualbox settings, but they are greyed out and I cannot 'tick' them.

I am running an xp virtualbox on a ubuntu 9.10 os.

---

### Post by arma0012 on 2010-04-10
It's working now, I had to uncheck 'Enable USB 2.0 (EHCI) controller' in the usb device settings panel in the virtualbox settings.

---

