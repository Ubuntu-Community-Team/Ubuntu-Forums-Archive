---
title: "Help needed restoring a broken GFX environment!"
date: 2009-11-24
forum: General Help
---

### Post by KONEY on 2009-11-24
Hello all!

I had some serious system problems after upgrading to 9.10 and trying to install some Ati graphix drivers.

I need to resolve thing one at time, so **I'm begging** for help to fix the display now!

This is the scenario, ubuntu boot into shell and I need to manually startX. Xorg installation is broken and since I was not able to fix it in anyway I changed the graphix drive inside xorg.conf to "vesa". Now I can see my desktop but of course it's all blurry and slow...

Has anyone time to point me to a procedure to restore the drivers?

thanx!

---

### Post by dcstar on 2009-11-24
> **KONEY said:**
> Hello all!

I had some serious system problems after upgrading to 9.10 and trying to install some Ati graphix drivers.

I need to resolve thing one at time, so **I'm begging** for help to fix the display now!

This is the scenario, ubuntu boot into shell and I need to manually startX. Xorg installation is broken and since I was not able to fix it in anyway I changed the graphix drive inside xorg.conf to "vesa". Now I can see my desktop but of course it's all blurry and slow...

Has anyone time to point me to a procedure to restore the drivers?

thanx!

System-Administration-Hardware Drivers

PS - Update your forum profile for 9.10

---

### Post by KONEY on 2009-11-24
Signature updated, thanx for reminding!

*System-Administration-Hardware Drivers *says "No proprietary drivers are in use on this system" and I can do anything else (all empty)

---

### Post by staf0048 on 2009-11-24
This worked for me when I was having problems with my ATI driver.

> Open up the terminal and do:

```

sudo apt-get remove --purge xorg-driver-fglrx
```
-Enter your password and hit Enter.

That'll get rid of any installed packages relating to the ATi Driver.


   1.  Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
   2. With super user permissions, enter the command "sh ./fglrx-uninstall.sh" 

to do that in the terminal run:

```

cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh

```


Hope this helps you.

---

### Post by KONEY on 2009-11-24
Thanx,

xorg-driver-fglrx was already purged while sh uninstall outputs:

koney@BEAST2-UBUNTU:/usr/share/ati$ sudo sh ./fglrx-uninstall.sh
restore of system environment completed
Uninstall fglrx driver complete...

What next?

---

### Post by staf0048 on 2009-11-24
You should have a workable system now, without any propietary drivers.  I no longer use 9.10 (due to bugginess on my laptop) so I'm not sure if this is still available, but I've always used "envyng" to install and configure my ATI driver properly.  

Search for it in Synaptic.  Last I used it the graphical side of it was broken, so you had to start it with:

```

envyng -t

```

---

### Post by JBAlaska on 2009-11-24
What ATI card are you using?

**Edit: I would advise against using envyng to install ATI drivers on 9.10**

---

### Post by KONEY on 2009-11-24
Thanx guys!

Actually the system is usable but has a lot of problems, the boot stops at prompt so I have to startx manually (many other things don't work, like audio, but I'll see them later)

I have a EAH4350 Silent. Was working properly under 9.04. 

If envyng is not suitable for 9.10 what would suggest?

---

### Post by JBAlaska on 2009-11-24
Try this to get the proprietary drivers to install:

Go to system, administration, software sources and make sure "proprietary drivers for devices" is checked. Start a terminal and type:
```
sudo apt-get update
```

Boot into the recovery kernel from the grub menu and choose the fix x option. resume the boot, when you get to the desktop run update manager and install any updates. reboot. 

Then go to System, Administration, "Hardware Drivers" and see if the ATI driver is listed for install, and enable it. If it still does not show up, post back here and we will try something else.

---

### Post by KONEY on 2009-11-25
Ok, thanx!

system, administration, software source says:
[I]Failed to run /usr/bin/software-properties-gtk as user root.
Unable to copy the user's Xauthorization file[/I]

To prevent this I have to run startx with sudo (losing all my setting). Anyway "proprietary drivers for devices" is checked.

I can't see any  "fix x option" in the recovery menu...am I blind?

Anyway under "Hardware Drivers" I can see an ATI driver not activated. When I try to activate it something happens but after the driver is still "not activated"...

---

### Post by JBAlaska on 2009-11-25
You seem to have a permissions problem as well as your other troubls. The way I see it, at this point you have two options:
1- Do a fresh install of 9.10 instead of the upgrade I assume you have done. This may be the best bet since it seems other things are broken.

2- Try to fix your current problem.

The first step on this road (before we mess with your sudoers file) is to run this command:
```
ls -la ~/ | grep .Xauth
```

If the output of this shows root instead of your user name...that's the problem.
In this case you would run:
```
sudo chown username:username ~/.Xauthority
``` Where username obiviously is your username.

Post back and we can go from there.

I have a short job today, and will be back in about an hour.

---

### Post by KONEY on 2009-11-25
OK!

```

koney@BEAST2-UBUNTU:~$ ls -la ~/ | grep .Xauth
-rw-------  1 root  root       0 2009-11-20 22:09 .Xauthority
koney@BEAST2-UBUNTU:~$ sudo chown username:koney ~/.Xauthority
[sudo] password for koney: 
chown: invalid user: `username:koney'
koney@BEAST2-UBUNTU:~$ sudo chown koney:koney ~/.Xauthority
koney@BEAST2-UBUNTU:~$ 

```

Now I can access software sources and synaptic again! Seems like we're going somewhere ;)

---

### Post by JBAlaska on 2009-11-25
Great, Now see if you can install the propritary ATI driver through Hardware drivers, but just to be sure run:
```
sudo apt-get update
sudo apt-get upgrade
```

Then try going to Hardware drivers and enabling the recommended ATI driver.

---

### Post by KONEY on 2009-11-25
Same thing, they silently don't activate at all....

---

### Post by JBAlaska on 2009-11-25
Darn..I hate "silently" lol. You can try installing the new Catalyst driver from the ATI site, but then you will have to reinstall the driver when there is a kernel upgrade, no big deal but a pain none the less.

Lets try one more time first. I think you already did this first step early in this thread, but just to be sure:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

Then Do:
```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```

Make sure you have the correct version of libGL.so and libglx.so:
```
sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core
```

Try the hardware drivers enable after a reboot.

If this does not work, let me know if your running 32 or 64bit Ubuntu and I can help you install the Catalyst drivers from the ATI website.

---

### Post by KONEY on 2009-11-25
Man...upgrading the kernel is nearly as dropping a bomb on your motheboard...audio dont' work, video don't work and firefox' fonts look all blurry (something that mac users call "antialiasing" and that they experience by default, with no need to upgrade the kernel :)))

Anyway I did all, startx didnt work of course so I manually forced vesa inside xorg.conf. Now I'm in desktop again, did the hardware activation thing but after a download still a silent exit...

I wonder..is there a command line command to issue this action so it's maybe possible to see verbosely what's wrong?

---

### Post by JBAlaska on 2009-11-25
So hardware drivers did the download driver thing? have you tried rebooting after that and seeing if hardware drivers now shows the ati driver enabled?

You can open synaptic package manager and see if these are all installed:
```
xorg-driver-fglrx 
fglrx-amdcccle 
fglrx-kernel-source 
xorg-driver-fglrx-dev
```

If they are, try doing:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Other than that I'm starting to run out of idea's other than doing a complete install of 9.10. I haven't messed with ati personally since I had a 9800 XT since Nvidia plays much nicer with Linux.

---

### Post by Divider on 2009-11-25
try the proprietary drivers from ati's website. you can do it one of 2 ways. I recommend building the module specificity for ubuntu 9.10.
Download it with firefox or if you can't get X to work, use w3m.

for firefox download.
```
cd Downloads/
```

Then.

```
sudo sh ati-versionnumber-linux-blah-blah.run --buildpkg Ubuntu/karmic
```

install the fglrx, the ccc, and the kernel module .deb's. if the kernel module returns its already installed your all good.

do an:
```
sudo aticonfig --initial 
```

to generate a meager xorg.conf and you should have not only some nice working drivers, but also 3d support. 
**Give it a reboot.**
and good luck.

---

### Post by KONEY on 2009-11-25
I tried both methods. Everything installs properly (now I see a good display) but the driver still can't be activated (I guess it's using a generic now because everything is sloooow)

---

### Post by KONEY on 2009-11-29
Some little updates: I made a fresh install of 9.10 and YES, my driver activted! But after I re-installed it because grub was not properly configured, and now on the new fresh install it doesnt activate again....NOOOOO! :)

---

### Post by efflandt on 2009-12-05
What type of monitor are you using, how is it connected (VGA or DVI/HDMI), and does **Failsafe GNOME** work (from dropdown list, if you get to gui login screen)?  What does **sudo lspci -v** show related to your video card?

I had an issue with "splash" when using widescreen HDTV on DVI.  After the grub2 menu, it would flash a cursor for 1 second, then black screen (nothing further and no disk activity).  Although, recovery boot got me to a prompt where startx worked, or manually entering grub2 commands got me to gui login (my ATI card works with default kernel radeon default xserver-xorg-server-ati and xserver-xorg-server-radeon).  The solution in that case was to remove "splash" from boot by using **sudo nano etc/default/grub** to comment out #GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and instead use GRUB_CMDLINE_LINUX_DEFAULT="quiet" (then **sudo update-grub** after saving that).

I had a different issue with older ATI card on an old system using VGA.  X in that system did not work after first updates in Xubuntu 9.10, and did not work at all in Ubuntu 9.10 except in Failsafe GNOME.  So for Xubuntu I had to us Synaptic to install **xorg-driver-fglrx** before doing any updates, or from Failsafe GNOME in Ubuntu before I could even get into X.  But Failsafe GNOME has limited capabilities (inability to configure networking) so you need an automatic network connection (wired dhcp) to network install packages.

I also notice **xserver-xorg-server-radeonhd** package in Synaptic that may help newer ATI cards.  Canonical does not provide updates for xserver-xorg-video-radeonhd. Some updates may be provided by the Ubuntu community.

---

