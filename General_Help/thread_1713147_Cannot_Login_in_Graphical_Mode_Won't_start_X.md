---
title: "Cannot Login in Graphical Mode/ Won't start X"
date: 2011-03-23
forum: General Help
---

### Post by lordjj on 2011-03-23
Hi. I'm having a problem booting Ubuntu. Last time I used Ubuntu I did 2 things that might have caused this:

1- I added a repository to my software sources:
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu (lucid main #xorg-edgers PPA)
deb src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu (lucid main #xorg-edgers PPA)
```
and updgraded the  intel graphics packages:
xserver-xorg-video-intel
xserver-xorg-video-i740
 (I wanted to update the driver for my Integrated  Mobile Intel 4 Series Express Chipset (rev07) )

2- I added languages to the locale folder (although no files were overwritten)

After this, when I boot it would completely freeze at log in screen (not even cntrl-alt-f1 works).

First thing I tried was to enter recovery mode, remove the last added repo using:
```
sudo nano /etc/apt/sources.list
```
deleting those lines and saving the file.
Then, I did:
```
sudo apt-get remove xserver-xorg-video-intel
sudo apt-get remove xserver-xorg-video-i740
```
then
```
sudo apt-get install xserver-xorg-video-intel
 sudo apt-get install xserver-xorg-video-i740
```

I assume this should have reverted the drivers to their old version.

Anyway, after this, when I log in, it doesn't even go into graphical mode anymore and just shows me this:
```
...
*Starting AppArmor profiles | skipping profile in /etc/apparmor.d/disable/:usr.bin.firefox
*Setting sensor limits
*Loading cpufreq kernel modules ...
*CPUfreq Utilities: Setting ondemand CPUfreq governer ...
*CPU0
*CPU1

cannot open locale definition file 'en_US.utf8': No such file or directory

*speech-dispatcher
...
*checking battery state
```

And stops there, and doesn't continue into graphic mode.

If I try:
```
startx
```

I get an error including:
```
md5sum: etc/X11/xorg.conf: No such file directory
[...]
(EE) module ABI version (6) doesb't match the server's version (7)
(EE) Failed to load moduke "fdev" (module requirement mismatch, 0)
(EE) No drivers available

Fatal server error: no screens found

check "/var/log/Xorg.failsafe.log" for additional info
```

Can you help me this? Also if "/var/log/Xorg.failsafe.log" could be useful, can someone tell me how to mount a hard drive or inserted USB dive through terminal and use "cp" to copy to that location?

Any help would be appreciated thank you.

---

### Post by lordjj on 2011-03-24
I deleted the whole X11 folder and Reinstalled xserver-core, and I'm back in business! :D
```
rm -r /etc/X11
sudo apt-get remove xserver-core
sudo apt-get install xserver-core
```

---

