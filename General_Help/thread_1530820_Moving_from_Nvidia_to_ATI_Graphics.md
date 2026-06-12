---
title: "Moving from Nvidia to ATI Graphics"
date: 2010-07-14
forum: General Help
---

### Post by Jimbo8098 on 2010-07-14
I have recently moved from an Nvidia 9400 GT to a ATI HD 5670 but im having a little trouble getting ubuntu to run properly with the new graphics card. I have uninstalled all of the old installed graphics drivers for my nvidia card and have tried to install all of the ati ones. Heres a list of what I have installed:

X.Org X Server -- AMD/ATI display driver wrapper (xserver-xorg-video-ati)
X.Org X Server -- AMD/ATI Radeon Display Driver (xserver-xorg-video-radeon)
Video driver for the ATI graphics accelerators(fglrx)
Catalyst Control Centre for the ATI graphics accelerators (devel symbols)(fglrx-dev)
X.Org X Server -- AMD/ATI Radeon Display Driver (debugging symbols)(xserver-xorg-video-radeon-dbh)
X.Org X Server -- ATI Mach64 display driver(xserver-xorg-video-mach64)
X.Org X Server -- ATI r128 display driver(xserver-xorg-video-r128 )
Identifiers supported by the ATI graphics Driver(fglrx-modaliases)

I am typing this from failsafex graphics mode in recovery mode , it starts up with a message saying:

(EE)RADEON(0) : Acceleration initialization failed
(EE)GLX error : Can not get rquired symbols

Botting to generic causes the os to boot (I can hear sounds) but when i get to where the desktop is SUPPOSED to be my screen says that the signal is over range. I have not changed my display in years so i am guessing that this is a driver incompatability.

I have heard of things like needing certain drivers but i have not had a full explanation since i am an ubuntu n00b :) I can install games and use the console but apart from that im a windows mover :)

Thanks in advance!

Jimbo8098

-----------------------------

EDIT - Hmm got it booting into generic by removing the mach64 and r128 drivers BUT during my initial test i cant enable extra visual effect or play any game seemingly. Im sure this points to something. I will boot to safegraphics and see if it gives any errors

EDIT2 - Removing those 2 gave me new error message at startup of failsafe:

(EE)Failed to load module "ati" (module does not exist,0)
(EE)GLX error : Can not get required symbols

Ive ran out of ideas... anyone else?

---

### Post by dcstar on 2010-07-14
> **Jimbo8098 said:**
> I have recently moved from an Nvidia 9400 GT to a ATI HD 5670 but im having a little trouble getting ubuntu to run properly with the new graphics card.
.......
Ive ran out of ideas... anyone else?

Rename the /etc/X11/xorg.conf file and reboot.

---

### Post by Jimbo8098 on 2010-07-14
> **dcstar said:**
> Rename the /etc/X11/xorg.conf file and reboot.

Could you instruct me more in this? Rename the file to what?

---

### Post by Grenage on 2010-07-14
To anything else, I suggest xorg.conf.old.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

---

### Post by Jimbo8098 on 2010-07-14
> **Grenage said:**
> To anything else, I suggest xorg.conf.old.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

K Ill try that when i get home :)

---

### Post by Jimbo8098 on 2010-07-14
When i do thins in failsafe mode i get a message saying file could not be located.

i typed in "sudo mv [and so on]"

---

### Post by Grenage on 2010-07-16
Ok, then you just don't have one (that's the norm now).  What's your monitor make/model, and desired resolution?

---

### Post by Jazzy_Jeff on 2010-07-16
After you get this fixed I would recommend that you stay with nvidia when you purchase new cards. They seem to be better supported. I have never had any issues with them at all. Can't say the same for ATI.

---

### Post by llawwehttam on 2010-07-16
ATI seem to be very careless with their linux drivers. The nvidia proprietary ones work much better.

Sorry I can't help more with your issue. I had a similar problem a while ago and ended up just changing cards.

---

### Post by digitalcitizenx on 2010-07-16
> **llawwehttam said:**
> ATI seem to be very careless with their linux drivers. The nvidia proprietary ones work much better.

Sorry I can't help more with your issue. I had a similar problem a while ago and ended up just changing cards.

I agree with this poster.

---

### Post by clhsharky on 2010-07-16
Jimbo8098

Install fglrx driver. Its the correct driver for your card at the moment.

System> Administration>Hardware Drivers
Make sure fglrx-modaliases is installed before going to hardware drivers.
IF You have installed fglrx and its not working then
```
sudo aticonfig --initial
sudo reboot
```
or install from terminal
```
sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev
sudo aticonfig --initial
sudo reboot
```
Then add Catalyst Control Centre.

The drivers
> Org X Server -- AMD/ATI display driver wrapper (xserver-xorg-video-ati)
X.Org X Server -- AMD/ATI Radeon Display Driver (xserver-xorg-video-radeon)
X.Org X Server -- AMD/ATI Radeon Display Driver (debugging symbols)(xserver-xorg-video-radeon-dbh)
X.Org X Server -- ATI Mach64 display driver(xserver-xorg-video-mach64)
X.Org X Server -- ATI r128 display driver(xserver-xorg-video-r128
Are default OSS drivers and don't support acceleration on ATI HD5xxx cards yet. No need to remove, fglrx bypasses them.



Sharky

---

