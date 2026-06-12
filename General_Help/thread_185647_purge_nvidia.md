---
title: "purge nvidia"
date: 2006-06-01
forum: General Help
---

### Post by LORD_PoLvO on 2006-06-01
hello, can anybody please help me with something?
i have tried and failed with installing nvidia drivers and have messed up so i need to completely purge my computer of all nvidia drivers, i can backup to xorg because i fogot to back it up before i started... lol. well anybody know how to completely purge nvidia drivers?

---

### Post by Zdravko on 2006-06-01
That is an interesting topic. Although I have not Dapper yet, I may have troubles with the drivers later. A brief and accurate desciption of the solving could be of use.

---

### Post by LORD_PoLvO on 2006-06-01
yuppers :) im not truley a dapper user yet i still have my breezy as a fallback when i need to lol.

---

### Post by codejunkie on 2006-06-01
[quote=LORD_PoLvO]hello, can anybody please help me with something?
i have tried and failed with installing nvidia drivers and have messed up so i need to completely purge my computer of all nvidia drivers, i can backup to xorg because i fogot to back it up before i started... lol. well anybody know how to completely purge nvidia drivers?[/quote] open a terminal and enter or copy and paste this into it
```
sudo apt-get remove --purge nvidia*
``` this completely removes the drivers installed thru synaptic,
then enter or copy and paste this into a terminal
```
sudo nvidia-installer --uninstall
``` this will remove anything installed if you used the .run package from [www.nvidia.com]("http://www.nvidia.com") hope this helps.

codejunkie

---

### Post by kvonb on 2006-06-01
I had MAJOR nVidia problems with Dapper too, I have a Geforce2 MX400.

Mine was complaining about different kernel module versions, but works well now.

Here is what I would do:

sudo gedit /etc/X11/xorg.conf

change the driver line under Section "Device" from "nvidia" to "nv", save and quit.

Run synaptic (Menu: System -> Administration -> Synaptic Package Manager)

Search for nvidia

Remove any nvidia-glx packages, nvidia-settings

Make sure that xserver-xorg-driver-nv is still there, install if not.

Quit synaptic, logout, press ctrl-alt-backspace to restart X, you could reboot if you want.

You should be in vanilla nVidia mode now, these are the instructions I followed:

The NVIDIA drivers are in the "restricted" section of the Ubuntu Package repository, so before you will be able to install the drivers, you must enable this section on your system.

   1.  Select the System menu at the top of the screen.
   2.  Select Administration then Synaptic Package Manager.
   3.  In the package manager, select the Settings menu, then Repositories.
   4.  In the Software Sources dialog that comes up, click the Add button.
   5.  In the Edit Repository dialog, ensure that the Restricted copyright box is checked, then press OK.
   6.  Press OK to close the Software Sources dialog, when Synaptic asks you to reload the package database, say yes.

You now have access to the many additional packages in the restricted section, including the NVIDIA driver packages.
Install and activate drivers

Packages may be installed by right-clicking on the package and selecting Mark for Installation.

   1.  Click the Search button and search for "nvidia".
   2.  If your card is a TNT, TNT2, TNT Ultra, GeForce1, or GeForce2*, then install nvidia-glx-legacy, otherwise install nvidia-glx.
   3.  If you are running Hoary Hedgehog or Breezy Badger, then install nvidia-settings. DO NOT install nvidia-settings in Dapper Drake because it will remove nvidia-glx.
   4.  Click the Search button and search for "linux-restricted-modules". You must have restricted modules enabled (see above).
   5.  Find the appropriate module for your kernel. For example, if you have linux-image-amd64-k8 installed, then you should install linux-restricted-modules-amd64-k8.
   6.  Click the Apply button to install the new packages.
   7.  Once Synaptic has finished applying your changes, exit the application.
   8.  Select the Applications menu at the top of the screen, then Accessories, then Terminal.
   9.  In the terminal window, type the following:

sudo nvidia-glx-config enable (if you get an error, just edit the file with sudo gedit /etc/X11/xorg.conf, search for "nv" and change it to "nvidia"

   1.  Close all your applications, then press Ctrl-Alt-Backspace to restart the X server. If you see an NVIDIA splashscreen after hitting Ctrl-Alt-Backspace, your drivers are properly installed.

* I have a Geforce2 MX400 and I am using non-legacy drivers, I think the problem is that there are no updated drivers for Dapper and the legacy cards!

Good luck :)

---

### Post by tseliot on 2006-06-01
try with:
sudo apt-get --purge remove nvidia-glx nvidia-settings linux-restricted-modules-`uname -r` nvidia-kernel-common

---

### Post by gwilson on 2006-06-01
I'm not a guru, but you guys might want to verify what kernel version is being loaded by GRUB. My system downloaded the newest kernel (2.6.15-23-) but GRUB continued to load the older kernel (2.6.15-21-) due to the way my system was set up. I don't think the 21 kernel supports the newest version of the nvidia driver. You might want to do a "sudo update-grub" in a terminal window. The system will search out all of the available kernels and operating systems and update your /boot/grub/menu.lst file. It will find the 23 kernel and make it available for you to select when the GRUB menu comes up when you boot the computer. Doing this and selecting the newest kernel 23 solved all of the nvidia problems I had following the most recent update of Dapper.

---

