---
title: "lubuntu-desktop, chromium-browser l10n dependency, ignore?"
date: 2010-11-08
forum: General Help
---

### Post by Takenover83 on 2010-11-08
I have done a base install of ubuntu 10.10 via mini.iso on my Powerbook G4. I want to install lubuntu, but I hit a speed bump.

```
sudo apt-get install lubuntu-desktop
```
```
The following packages have unmet dependencies:
 lubuntu-desktop : Depends: chromium-browser-l10n but is not going to be installed
E: Broken packages
```

I tried adding -f, but it did not help. I could care less about chromium as I know it is not supported on powerpc. I will gladly install firefox. I want to ignore the error and continue installing without chromium.

---

### Post by Takenover83 on 2010-11-08
Hmmm, anyone? I know this doesn't have everyone stumped. I figured it was a simple fix, that eluded me.

---

### Post by Takenover83 on 2010-11-08
Bump, last try.

---

### Post by a.panico on 2010-11-09
Hi,

In this [link]("http://packages.ubuntu.com/maverick/lubuntu-desktop"), you can see the packages that are included in the metapackage. So, you only have to copy the next code (I haven't included the packages that aren't available for powerpc):

```
$ sudo apt-get install abiword ace-of-penguins alsa-base alsa-utils anacron apport-gtk aqualung cheese cron cups-driver-gutenprint desktop-file-utils evince galculator gdebi gksu gnome-bluetooth gnome-disk-utility gnome-mplayer gnome-power-manager gnome-system-tools gnumeric gpicview gvfs-fuse hardinfo jockey-gtk language-selector leafpad logrotate lubuntu-core lxappearance lxdm lxinput lxlauncher lxpanel-indicator-applet-plugin lxrandr lxsession-edit lxshortcut lxtask lxterminal modemmanager mtpaint network-manager-gnome ntp obconf osmo pcmciautils pidgin pm-utils policykit-desktop-privileges ppp scrot simple-scan software-properties-gtk sylpheed sylpheed-i18n synaptic system-config-printer-gnome transmission ttf-liberation ttf-ubuntu-font-family ttf-unfonts-core ttf-wqy-microhei ubuntu-extras-keyring unzip update-notifier wireless-tools wpasupplicant wvdial x11-utils xarchiver xchat xdg-user-dirs xdg-utils xfburn xpad xscreensaver zip powernowd
```

I performed the installation with the mini.iso, so I have also installed the package xserver-xorg-video-nouveau for the graphics driver. 
It works, but at least for me (Powerbook6,8, 12" 1.5Ghz Geforce FX go5200 -nv34m-) the suspend function doesn't work, neither the graphics output neither the bright function keys. But it seems to work better than the nv driver for the 2D accel. I hope that one day nouveau will become stable and i can finally use the suspend function with GNU/Linux.....

If you have time, you can have a look to debian+lxde distribution ([Linux MintPPC]("http://www.mintppc.org/")). It's a script that you execute on top of a debian squeeze minimal installation, and it installs a lot of software and correct serveral bugs of powerpc, but for me the nouveau driver didn't work, so I had to change to the nv driver.

Good luck. Bye!

---

### Post by fixerdave on 2011-10-22
> **a.panico said:**
> ...
```
$ sudo apt-get ...
```
...

I know this is an old post but I just wanted to say thanks for this.  Having just tried 11.10 on my PPC minimac and not getting any joy, I decided to retrograde to what I know works.  Then I decided to go light... and got stuck again, sigh.  This worked for me.

---

