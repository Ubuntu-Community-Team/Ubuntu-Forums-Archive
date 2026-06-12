---
title: "64 bit Flash (youtube)+Broadcom Crystal HD in Oneiric?"
date: 2012-04-16
forum: General Help
---

### Post by kecsap on 2012-04-16
Hi,

I am just unable to make my Broadcom Crystal HD (BCM70012) with Adobe Flash Player (Firefox) work on a 64 bit Oneiric installation. I tried a few versions of the crystalhd driver (also bleeding edge), but while the HD playback is accelerated, flawless and fine in XBMC, the Adobe Flash Player does instant crash or fallback to software rendering when I start to play any youtube clip. The broadcom indicator on the panel shows the usage attempt of the card by Flash. The "dmesg | grep crystal" shows no error, the Flash Player opens the Crystal HD and closes after a few seconds.

Any help is appreciated from someone with working software setup for Crystal HD+Flash Player on 64 bit or 32 bit Oneiric. My laptop is a HP 2510p with Intel X3100, if it makes any sense to mention.

Edit1:
I have:
$ cat /etc/adobe/mms.cfg 
OverrideGPUValidation=1
EnableLinuxHWVideoDecode=1

Thanks

---

### Post by kcleong on 2012-04-17
Config in mms.cfg seems to be correct. I've the same setup but with a BCM70015 chip. I've installed the crystalhd module from apt-get, crystalhd-dkms and firmware-crystalhd should work.

Flash playback is ok except in fullscreen, which is annoying. :)

---

### Post by asuastrophysics on 2012-04-17
Flash player is the scorn of the Earth; the most revile, disgusting piece of software ever written...imo. Seriously though I really despise adobe...and flash player. Can't wait for all websites to use HTML5 ;)

Anyway, putting personal opinions aside...what video driver are you using? Is it a proprietary driver or is it an open-source driver?
You said you're using crystalhd. Is that the proprietary driver for your card?

---

### Post by kecsap on 2012-04-18
> **asuastrophysics said:**
> Flash player is the scorn of the Earth; the most revile, disgusting piece of software ever written...imo. Seriously though I really despise adobe...and flash player. Can't wait for all websites to use HTML5 ;)

Anyway, putting personal opinions aside...what video driver are you using? Is it a proprietary driver or is it an open-source driver?
You said you're using crystalhd. Is that the proprietary driver for your card?

Both crystalhd and intel video have open-source drivers installed since there is no other choices.

---

### Post by kecsap on 2012-04-19
It seems that I solved the situation with:

- Clone a git repository git://anonscm.debian.org/collab-maint/crystalhd.git, generate the debian packages and install them. Remove the old crystalhd kernel driver and reload the new.
- Downgrade the flash player version to 10.3. E.g grab is from [here]("http://pkgs.org/opensuse-11.4/opensuse-update-i586/flash-player-10.3.183.7-0.2.1.i586.rpm.html").
- Using OverrideGPUValidation=0 in /etc/adobe/mms.cfg, otherwise the fullscreen video playback does not work and black screen appears in this mode. So the mms.cfg looks like:

> OverrideGPUValidation=0
EnableLinuxHWVideoDecode=1


- To fix the permissions of the /dev/crystalhd dev node permanently, create a one-line file (20-crystalhd.rules) into /etc/udev/rules.d:

> KERNEL=="crystalhd", MODE="0666"


- Installing the CrystalHD indicator. I slightly modified with fixed icons+polling interval to 3 seconds. It can be downloaded from [here]("http://www.mediafire.com/?ritf3xo7ka5e9hb"). The indicator icon shows the actual status of the Crystal HD card and right-click on the icon provides a popup menu to turn on/off the card.
- When the crystalhd kernel driver is loaded when going to suspend, it is needed to reinit again after resume. Put the following file (80_crystalhd) into the /etc/pm/sleep.d:

> #!/bin/bash
case $1 in
hibernate)
;;
suspend)
;;
resume|thaw)
# Need to re-init the crystalhd after a resume
if [ `lsmod | grep -o ^crystalhd` ]
then
modprobe -r crystalhd
modprobe crystalhd
fi
;;
*)
;;
esac


Experiences:

- XBMC 11.0 from PPA: works.
- Adobe Flash Player 10.3: works.
- The Flash Player 11.x versions with Crystal HD are unstable. The playback starts, but after sometime, lags happen and I get problems with the crystalhd soon -> stalled and failed. In these cases, if Firefox freezes and if I kill the flash's plugin-container process, the whole system freezes, sometimes I get kernel oops during playback.
Results:

[B]When the laptop is suspended while the Crystal HD accelerates a Flash video, the Crystal HD card is not usable until the next reboot. Thus it is adviced to switch off the Crystal HD card via the indicator normally since it consumes some power and gives a lower risk to go suspend during playback. (E.g the Adobe Flash Player opens the 360p and 480p streams with the Crystal HD card, but it does not make any sense and results no help in the lower CPU consumption.)
[/B]

---

