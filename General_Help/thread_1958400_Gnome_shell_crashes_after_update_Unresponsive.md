---
title: "Gnome shell crashes after update? Unresponsive"
date: 2012-04-14
forum: General Help
---

### Post by Macfunky on 2012-04-14
Yesterday morning i booted up my computer (ubuntu 11.10 which i've been running successfully since it's release))having updated the system the previous day. It was the first boot up since the update which leads me to believe it's the reason for the problem. Anyway, it booted up into gnome shell. First thing i noticed was that my mouse froze. It would periodically unfreeze but refreeze again. The toolbar on top kept disappearing, then reappearing. It was so eratic that i was unable to do anything. The mouse wouldn't unfreeze long enough before freezing up again and anything i clicked on wouldn't respond. In the end i figured i'd just back up and reinstall. I did so but found myself having the exact same problem with a new install. I am wondering if this has something to do with the graphics driver being updated? And if so what can i do about it? I have a geforce 8800 gtx and use the recommended nvidia drivers. I eventually tried to install Xubuntu (fresh install). I am currently running it and keeping with it until i figure out what happened to gnome shell for me. Anyone have any ideas?

---

### Post by HKei on 2012-04-14
EDIT: Both problems were due to my own stupidity, and had nothing to do with any updates.

---

### Post by Otto69 on 2012-04-14
I have the same problem with Gnome 3 after update yesterday. Interesting is that my video card is NVidia GeForce 8800 GTS.

---

### Post by Macfunky on 2012-04-14
> **Otto69 said:**
> I have the same problem with Gnome 3 after update yesterday. Interesting is that my video card is NVidia GeForce 8800 GTS.

I'm imagining it is something to do with graphics drivers changing in the update but i don't know what to do about it. I am using XFCE now (which i'm also quite fond of but i do prefer Gnome shell). I am afraid to try out Gnome shell again cause once i get into it i can't get out, my mouse and keyboard are almost useless. Have you tried Unity by any chance? I have my set up back to normal now with XFCE and don't want to try out anything more until i hear more about this issue. I reckon i would have the same problem in Unity?

---

### Post by Otto69 on 2012-04-14
I am working now on Gnome classic. Unity has also problems, KDE plasma works without 3D features. I have also tried with NVidia 173 driver, with same results. It is very strange, I have the same opinion: it is something wrong with NVIDIA-driver after the update from yesterday.

---

### Post by Macfunky on 2012-04-14
> **Otto69 said:**
> I am working now on Gnome classic. Unity has also problems, KDE plasma works without 3D features. I have also tried with NVidia 173 driver, with same results. It is very strange, I have the same opinion: it is something wrong with NVIDIA-driver after the update from yesterday.

I hope it gets fixed soon. Do you know where i should file a bug for it?

---

### Post by Otto69 on 2012-04-14
> 
I hope it gets fixed soon. Do you know where i should file a bug for it? 	


No, not really.

I have installed Fedora 15 with the same nvidia driver version (280.13) on the same machine. On Fedora (updated and checked 10 min. ago) works Gnome 3 perfect! So it should be the problem of Ubuntu packages.

---

### Post by Macfunky on 2012-04-14
> **Otto69 said:**
> No, not really.

I have installed Fedora 15 with the same nvidia driver version (280.13) on the same machine. On Fedora (updated and checked 10 min. ago) works Gnome 3 perfect! So it should be the problem of Ubuntu packages.

After a bit more looking around i see that a few people have reported it on launchpad so we're not the only ones.

---

### Post by tfriske on 2012-04-14
Hi guys,

I had the same display problem with my graphics card GeForce 8800 GTS aftter the update of package "nvidia-current" from version "280.13-0ubuntu6" to "280.13-0ubuntu6.1". The Unity 3D window manager went very slow, showed graphics errors and even temproarily froze. But eventually I was able to manage to switch to TTY1 after some delay of 10 seconds or so by pressing CTRL+ALT+F1 to login and get things straight.

I can confirm that the new version from above package causes the graphics errors. My solution is to "pin" the package for the Debian package manager to the previous version that worked just fine. Therefore I fired up a text editor to create the arbitrarily named text file "nvidia" under "/etc/apt/preferences.d/nvidia". The content is as follows:

Package: nvidia-current
Pin: version 280.13-0ubuntu6
Pin-Priority: 1000

After saving the file I issued the following commands to downgrade to the previous version "280.13-0ubuntu6" of package "nvidia-current":

sudo apt-get install --reinstall nvidia-current
sudo shutdown -r now

For me this is a temporary workaround until the next LTS version 12.04 of Ubuntu is released.

---

### Post by UltraAnders on 2012-04-14
> **tfriske said:**
> Hi guys,

I had the same display problem with my graphics card GeForce 8800 GTS aftter the update of package "nvidia-current" from version "280.13-0ubuntu6" to "280.13-0ubuntu6.1". The Unity 3D window manager went very slow, showed graphics errors and even temproarily froze. But eventually I was able to manage to switch to TTY1 after some delay of 10 seconds or so by pressing CTRL+ALT+F1 to login and get things straight.

I can confirm that the new version from above package causes the graphics errors. My solution is to "pin" the package for the Debian package manager to the previous version that worked just fine. Therefore I fired up a text editor to create the arbitrarily named text file "nvidia" under "/etc/apt/preferences.d/nvidia". The content is as follows:

Package: nvidia-current
Pin: version 280.13-0ubuntu6
Pin-Priority: 1000

After saving the file I issued the following commands to downgrade to the previous version "280.13-0ubuntu6" of package "nvidia-current":

sudo apt-get install --reinstall nvidia-current
sudo shutdown -r now

For me this is a temporary workaround until the next LTS version 12.04 of Ubuntu is released.Hi, I have exactly the same issue, but I'm using 11.04. On Wednesday I installed updates to including one to package nvidia-173 along with kernal image 2.6.38-14. I also have an Nvidia 8800 GTS.

Would the downgrade solution be the same for me on 11.04, e.g. is the package version different? I tried the process, it didn't help ... although not I'm convinced it changed the package.

---

### Post by tfriske on 2012-04-14
Check whether the directory "preferences.d" exists. If not there should be the file "preferences" where you can configure package rules alternatively.

I made up the solution by reading the following infos:

1. [http://wiki.ubuntuusers.de/Apt-Pinning](http://wiki.ubuntuusers.de/Apt-Pinning)

2. [https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers)

The former article is written in German. It states in the red warning box that there is a bug in Ubuntu versions 10.04 and 11.04 regarding Debian Package manager configuration. The bug manifests itself in that it ignores the possibly existing directory "preferences.d" and suggests that one should fallback to to the file "preferences" instead.

---

### Post by UltraAnders on 2012-04-15
> **tfriske said:**
> Check whether the directory "preferences.d" exists. If not there should be the file "preferences" where you can configure package rules alternatively.

I made up the solution by reading the following infos:

1. [http://wiki.ubuntuusers.de/Apt-Pinning](http://wiki.ubuntuusers.de/Apt-Pinning)

2. [https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers)

The former article is written in German. It states in the red warning box that there is a bug in Ubuntu versions 10.04 and 11.04 regarding Debian Package manager configuration. The bug manifests itself in that it ignores the possibly existing directory "preferences.d" and suggests that one should fallback to to the file "preferences" instead.Thanks, the launchpad link was useful. The preference.d directory exists. I think the problem might be that packages are called 270.41.06-0ubuntu1.1 and 270.41.06-0ubuntu1 for Natty.

In the end, I was able to log into Classic Mode (No Effects) and use Synaptic. For the packages "nvidia-current" and "nvidia-173", under the "Package" menu there is an option "Force Version". Once I downgraded, I then used the "Lock Version" option.

Some instructions here:
[https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version](https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version)

It's probably only necessary to downgrade the package for the h/w driver being used, i.e. current or 173, but I did both to be safe. I'm using current.

---

### Post by Maintech on 2012-04-15
Same issue on my wife's computer. It has an Nvidia 8800 video card. I thought the system was corrupt and did a re-install and all was well until I updated the system. Now I am back to a non-responsive system. I decided to look in the forum to see if others were having any issues and found this thread. It is a definite bug. Is the Ubuntu bug team aware of this issue and working on it or is it something that we will have to take care of ourselves until 12.04 is officially released? Thanks.


Edit: By chosing 2d in the login screen it works without lockup. It would seem the 3d is the part giving the issues.

---

### Post by Macfunky on 2012-04-17
> **UltraAnders said:**
> Thanks, the launchpad link was useful. The preference.d directory exists. I think the problem might be that packages are called 270.41.06-0ubuntu1.1 and 270.41.06-0ubuntu1 for Natty.

In the end, I was able to log into Classic Mode (No Effects) and use Synaptic. For the packages "nvidia-current" and "nvidia-173", under the "Package" menu there is an option "Force Version". Once I downgraded, I then used the "Lock Version" option.

Some instructions here:
[https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version](https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version)

It's probably only necessary to downgrade the package for the h/w driver being used, i.e. current or 173, but I did both to be safe. I'm using current.

Tried looking for the "Force Version" option but it's greyed out for me. Has anyone heard anymore about this problem? I have been keeping an eye on the update manager but haven't seen anything relating to nvidia since.

---

### Post by UltraAnders on 2012-04-17
> **Macfunky said:**
> Tried looking for the "Force Version" option but it's greyed out for me. Has anyone heard anymore about this problem? I have been keeping an eye on the update manager but haven't seen anything relating to nvidia since.This is probably a suck eggs statement, but just in case: I needed to have the relevant package, e.g. "nvidia-current", highlighted (or possibly ticked) for this option to enable. I'm not in front of my Linux box so can't confirm which.

---

### Post by Macfunky on 2012-04-17
Doesn't show up for me either way

> **UltraAnders said:**
> This is probably a suck eggs statement, but just in case: I needed to have the relevant package, e.g. "nvidia-current", highlighted (or possibly ticked) for this option to enable. I'm not in front of my Linux box so can't confirm which.

---

