---
title: "after nvidia driver removal in Ubuntu 11.10, what to edit in the xorg.conf ?"
date: 2011-12-11
forum: General Help
---

### Post by james2b on 2011-12-11
I had the older nvidia-173 display driver installed and mostly working, except for some items in that nvidia-settings tool, so then I did try to install that nvidia-current driver which did not give a GUI desktop, so just had the run level 3 text mode. Then I removed that nvidia-current driver in the terminal mode, and did; sudo apt-get purge nvidia-current which also deletes the configuration files, so now it boots to a dark screen and I need to edit my; /etc/X11/xorg.conf file under the section listed as "Device" so nvidia is replaced with the basic default driver, and in the /etc/X11/xorg.conf.failsafe file it shows this driver; "vesa", so is that what I need to edit my real xorg.conf file to be able to boot to a 2D basic desktop session to then use that driver tool to re-install nvidia? And I do have gnome shell, and Mint Mate installed to boot to.

---

### Post by james2b on 2011-12-12
Update on this issue; I re-installed the nvidia-current display driver which is version 280.13 and all went well, but now only some of my desktop manager sessions will both boot up and fully function. Working now is gnome classic 2D, and Unity 2D, ( failing are Unity and gnome classic 3D, and that gnome 3 shell ). So do again go back to the older nvidia-173 driver, or should I try to download and install direct from [www.nvidia.com](www.nvidia.com) ?

---

### Post by sgage on 2011-12-12
> **james2b said:**
> Update on this issue; I re-installed the nvidia-current display driver which is version 280.13 and all went well, but now only some of my desktop manager sessions will both boot up and fully function. Working now is gnome classic 2D, and Unity 2D, ( failing are Unity and gnome classic 3D, and that gnome 3 shell ). So do again go back to the older nvidia-173 driver, or should I try to download and install direct from [www.nvidia.com](www.nvidia.com) ?

I would purge nvidia again, delete xorg.conf altogether (it is unneeded), get to a GUI and use jockey to install nvidia-current.

---

### Post by james2b on 2011-12-12
After attempting the install of nvidia-current driver version 280.13, it then only partially worked, the 2D desktops functioned, but not 3D, so I downloaded and tried to install the newest version 290.10 direct from NVIDIA, which did mostly complete install except to compile the nvidia kernel module. So I just did a removal of the current version, and re-installed nvidia-173 older version which does work with the 3D desktop sessions. I now have several DM to select at the login screen.

---

### Post by james2b on 2011-12-14
This newest nvidia driver has a nvidia-installer put in so that it can be run again to finish the driver install process. So do I just use the package manager to find those needed kernel source and other files to install so that it can build the nvidia kernel module needed to complete ?

---

### Post by james2b on 2011-12-19
I found this site as an unofficial source for the nvidia display drivers; [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric) , so if I do add that to the /etc/apt/sources.list file and save it, and then run sudo apt-get update, then try to install it from either the terminal or the package manager will that driver provide full Unity or gnome3 desktop function with 3D, not just 2D as the nvidia 280.13 did ? This looks like the newest nvidia driver version 290.10 which is also available direct from the nvidia web site. This computer is a older Gateway from 2006 with a nvidia GeForce 7300 GS video card.

---

