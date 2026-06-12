---
title: "upgraded to latest ati drivers and problems"
date: 2010-05-01
forum: General Help
---

### Post by ELD on 2010-05-01
Okay so i updated my Lucid install to have the 10.4 drivers from ati and i can no longer enable desktop effects and even scrolling in my firefox seems slow?

---

### Post by dcstar on 2010-05-01
> **ELD said:**
> Okay so i updated my Lucid install to have the 10.4 drivers from ati and i can no longer enable desktop effects and even scrolling in my firefox seems slow?

If you installed non-repository drivers then uninstall them.

---

### Post by ELD on 2010-05-01
> **dcstar said:**
> If you installed non-repository drivers then uninstall them.

Why, the newest drivers are from ATI. Which is where i installed from.

Edit > Uninstalled the drivers from the hardware drivers program and replaced with drivers from ati's website and it works fine now.

---

### Post by MrCloudHands on 2010-05-01
> **ELD said:**
> Why, the newest drivers are from ATI. Which is where i installed from.

Edit > Uninstalled the drivers from the hardware drivers program and replaced with drivers from ati's website and it works fine now.

How did you install the drivers? 

My system has the Radeon X1200 series graphics card, and I downloaded the driver as a .run file from ATI's website. I have no idea how to install it though!

Hope someone can help. Thanks! :)

---

### Post by Mark Phelps on 2010-05-01
> **MrCloudHands said:**
> How did you install the drivers? 

My system has the Radeon X1200 series graphics card, and I downloaded the driver as a .run file from ATI's website. I have no idea how to install it though!

Hope someone can help. Thanks! :)

That's because -- you can't.  Install those drivers, that is.

ATI dropped fglrx driver support for your card over a year ago.  Now, the only drivers that will work are the open source drivers and those are installed by default.  

If you force the installation of the drivers from the ATI site, that will corrupt your display, and you'll only have to end up removing them and replacing them with the open source drivers.

---

### Post by MrCloudHands on 2010-05-02
> **Mark Phelps said:**
> That's because -- you can't.  Install those drivers, that is.

ATI dropped fglrx driver support for your card over a year ago.  Now, the only drivers that will work are the open source drivers and those are installed by default.  

If you force the installation of the drivers from the ATI site, that will corrupt your display, and you'll only have to end up removing them and replacing them with the open source drivers.

Thanks for the help. If they are installed by default then why is the "Hardware Drivers" list empty? Can I manually install the open source drivers?

---

### Post by ELD on 2010-05-02
> **MrCloudHands said:**
> Thanks for the help. If they are installed by default then why is the "Hardware Drivers" list empty? Can I manually install the open source drivers?

Hardware Drivers lists proprietary drivers. The open source driver would not be listen there.

---

### Post by MrCloudHands on 2010-05-02
> **ELD said:**
> Hardware Drivers lists proprietary drivers. The open source driver would not be listen there.

I see. Be that as it may, there's another indicator that no ATI drivers are installed when I try to open "ATI Catalyst Control Center", and I get this message:

[I]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.[/I]

How can I install these drivers? anyone?

---

### Post by ELD on 2010-05-02
ATI Catalyst Control Center is a proprietary app that comes with the proprietary drivers, it will not work for the open source drivers as they are open source, provided by the community and installed by default.

---

### Post by BrokeMahPC on 2010-05-02
I think it would be best to take your system back to a clean start re: the drivers.
In ubuntu you cant just switch between drivers with a click of the mouse in Hardware Drivers - you need to purge/uninstall fglrx (ATI proprietary) to get back to radeon (open source). Radeon is the default driver and is installed when you install ubuntu - it's just there and mostly just works! You normally don't have to do anything, as your card is not supported you can't install fglrx.
(if ATI catalyst is still on your system it's a sign you didn't uninstall fglrx)

do this:
Problem: Need to purge -fglrx
Typically, the following manual commands will properly uninstall -fglrx:

sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg

If you want desktop effects (compiz or KDE) you'll need the glx module loaded. This
will not work even after purging fglrx since a hanging libglx.so file is left around.
Both fglrx and xserver-xorg-core provide this file so to replace it with the correct
version you'll need to reinstall xserver-xorg-core as well.

sudo apt-get install --reinstall xserver-xorg-core
_reboot_ the pc.

or this:

Problem: Need to fully remove -fglrx and reinstall ati (radeon) from scratch
Here is a more aggressive recipe which removes both -fglrx and -ati, and reinstalls the latter:

sudo /usr/share/ati/fglrx-uninstall.sh # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

Then _reboot_ (or fix up the kernel modules and restart gdm)

---

### Post by Jean-Joey on 2010-06-03
Hello All..
I have a Dell studio 15 laptop that comes with ATI 3450 mobility radeon card..
After installing the Lucid Lynx, I faced problems with the ATI driver (which I installed via the hardware menu) SO I had to remove it using the same way and I'm using my laptop normally but without any OpenGL stuff.
PLUS, which is important for me, without any power-save feature to my Graphic card so my battery doesnt last like I'm using M$ windows..

Now, I heard from the news that ATI made a newer driver for Lucid lynx and fixed all the bugs..
How can I install/ use this new driver in my machine? the Proprietary driver from the H/W menu seems like no change, with all the same errors

Any help? 
Thanks in advance

---

### Post by ELD on 2010-06-03
@Jean-Joey it is always best to make a new post for a different problem and not update an old thread.

But the best way to install is via downloading the latest drivers from the ATi website.

---

### Post by Jean-Joey on 2010-06-03
> **ELD said:**
> @Jean-Joey it is always best to make a new post for a different problem and not update an old thread.

But the best way to install is via downloading the latest drivers from the ATi website.

Well, I think its the same problem here.., isnt it? (+ I listed another prob in a new thread. No one replied and it was removed as I remember)
Thanks for your reply. But I'm new to the driver stuff and the last time I downloaded and installed a driver from ATI it ruined the other one and I had to uninstall the LYNX to be able to use the laptop.

So, kindly help me step by step..
Current position: I can activate the driver. but dont know if it'll download the newest driver or the old one.
Note that I tend to use S/W provided by Ubuntu cuz its safer..

Any suggestions after downloading the driver from ATI? Is there's anyway to download the driver using the Ubuntu repositories (The easy way. like Installing a program??)
I need an expert help in this Issue to close it forever and fully enjoy playing with the Lynx :D

Thanks a lot in advance..:)))

---

### Post by ELD on 2010-06-03
There is no way to do it via repositories, the latest version is always via the ati drivers website.

Download it and run the installer, make sure you download the right one for your hardware and the installer does it all for you, it can't get much simpler.

---

### Post by Jean-Joey on 2010-06-04
> **ELD said:**
> There is no way to do it via repositories, the latest version is always via the ati drivers website.

Download it and run the installer, make sure you download the right one for your hardware and the installer does it all for you, it can't get much simpler.

Thats "Exactly" what I did last time and it ruined my OS.. I downloaded and run the installer!!!
Is there's any previous steps like uninstall the last driver permanently, changing a setting or something with Fglrx?
PS: what's exactly the difference in technology between the fglrx and the new driver??

Thanks..,
Greetings, Jean

---

