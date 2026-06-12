---
title: "Update caused screen or video problem"
date: 2011-04-13
forum: General Help
---

### Post by mattasus on 2011-04-13
I have an ASUS x50Z with an ATI Radeo HD 3200 and since I rebooted after doing the last update, yesterday my screen is not the same. Words are more fuzzy and everything is in widestretch. It's al most as if my driver got downgraded. I'm new to ubuntu and I need some help to identify and resolve the problem. Help would be greatly appreciated.

Btw, in an attempt of killing two birds with one stone, whenever I type a message, my cursor often get jammed up after highlighting part of the text or my typing jumps back in the text into random places. This happens in every application and it's very annoying. I've had this problem both times after completely installing Ubuntu.

---

### Post by seawolf167 on 2011-04-14
Whenever the kernel is updated on your *nix system, it will usually break the video drivers. You'll need to first uninstall the fglrx drivers, then reinstall the new graphics drivers for your card.

[Here ]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")is the how-to for uninstalling them drivers, as for the install, either System -> Administration -> Hardware Drivers, or download the proprietary suite from ATI/NVidia

---

### Post by mattasus on 2011-04-15
Thanks for your help! I ran the five commands that are in the link you gave me, which uninstalls and reinstalls everything and then I rebooted. But it didn't solve the problem. 
Anything else it can be?

---

### Post by seawolf167 on 2011-04-15
After you uninstalled the fglrx drivers did you install the new graphics drivers for your device?

---

### Post by mattasus on 2011-04-15
I copied this from the link you sent me. The first command said it did not exist and I did not do the last command. Is there something else I was supposed to do?

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
Optionally, if you want the proprietary fglrx/Catalyst driver to be installable through the Restricted Hardware Driver Manager (a.k.a. jockey), you'll need to:

  sudo apt-get install fglrx-modaliases
Then reboot (or fix up the kernel modules and restart gdm).
```

---

### Post by seawolf167 on 2011-04-15
You don't want to copy and run the "# (if it exists)" part.

Try running the either of the two previous commands in the link to see what fglrx drivers exist on your system

```
dpkg -l '*fglrx*'
-or-
locate fglrx
```

---

### Post by mattasus on 2011-04-15
I ran the command ```
sudo apt-get remove --purge fglrx*
```and I got ```
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Then I put in the apt-get autoremove and it tells me I need root permissions to do so. Am I supposed to do that?

---

### Post by mattasus on 2011-04-15
I'll be more specific and I'll show you everything I got from running the first 2 commands in the provided link and the cammand that you sent me.
```
yudeny@yudeny-F5Z:~$ sudo apt-get remove --purge fglrx*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Package fglrx-modaliases is not installed, so not removed
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
yudeny@yudeny-F5Z:~$ locate fglrx
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/doc/fglrx-modaliases
/usr/share/jockey/handlers/fglrx.py
/usr/share/jockey/handlers/fglrx.pyc
/usr/share/jockey/modaliases/fglrx-modules.alias.override
/var/lib/dpkg/info/fglrx-modaliases.list
/var/lib/dpkg/info/fglrx-modaliases.md5sums
yudeny@yudeny-F5Z:~$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-ati* xserver-xorg-video-radeon*
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 1,470kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148960 files and directories currently installed.)
Removing xserver-xorg-video-ati ...
Removing xserver-xorg-video-radeon ...
Purging configuration files for xserver-xorg-video-radeon ...
Processing triggers for man-db ...

```

---

### Post by mattasus on 2011-04-15
I since rebooted my laptop and as it rebooted it was checking c drive for errors but nothing else appeared after. The good news is that my screen is back to normal.
But I didn't reinstall anything so ???

---

