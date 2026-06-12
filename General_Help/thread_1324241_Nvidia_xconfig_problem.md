---
title: "Nvidia xconfig problem"
date: 2009-11-12
forum: General Help
---

### Post by milenixloerdi on 2009-11-12
Hi,

I used to run Ubuntu 9.10 as an installation within windows. Everythign was excellent - nvidia recognised, printer, camera, network....no problem at all.

I decided to partition and install clean - as a 2nd OS. Now, my nvidia doesnt seem to be recognised  by the automatic update manager. I try to copy and run the nvidia .deb packages from another computer and it said I already have them installed. _Still_, when I try "Display properties" this comes out:

**"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "**

I tried to run this command typing sudo nvidia-xconfig but it doesnt even let me type my password - the keyboard seems to "shut down" once the pass request is listed in the terminal window.

On my within windows installation it automatically recognised I need "additional drivers" for Nvidia (the icon poped-up on the pannel next to the clock, however on my clean install nothing like this happened.

I an, very new and Im sorry if I ask something...not too clever. However, I'd like to use Ubuntu instead of windows - I, also, do not believe in the "windows" mentallity and Im trying to do somethign about it, on my level :)

Please, someone help!

---

### Post by Giblet5 on 2009-11-12
When you execute ```
sudo nvidia-xconfig
``` the sudo command will prompt you for your password.

Type in your password - nothing will echo - then hit Enter. The shell prompt will come back.

Now you're ready to restart Xorg. You can either reboot, or run this in the same terminal window: ```
sudo /etc/init.d/gdm restart
```

That will log you off and return you to the login screen. The nvidia driver will now be in use.

---

### Post by milenixloerdi on 2009-11-12
Thank you so much, Giblet5! :) It didnt give me the restart command that you typed - it worked perfect :D

Thanks again!!!

---

