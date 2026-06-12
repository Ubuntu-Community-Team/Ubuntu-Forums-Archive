---
title: "HOWTO: install or uninstall nVidia drivers"
date: 2011-02-13
forum: General Help
---

### Post by linuxsyst on 2011-02-13
To install the drivers simply click:
System > Administration > Hardware Drivers


and enable/disable the recommended/enabled version.

However I belive that you will still need to restart the gmd for it to start working properly. Before you procede save all your work because your GUI will restart. Now type:

```
sudo /etc/init.d/gdm restart
```

[CENTER][SIZE="3"]Older HOWTO[/SIZE][/CENTER]

This is a short and simple guide that will show you how to install and uninstall nVidia drivers. The simplest way known to me is using EnvyNG, You can install it by opening terminal ```
(Alt+F2 then type gnome-terminal) and typing following:

sudo apt-get install envyng-gtk
```

When installation is complete start it with Alt+F2 then type envyng-gtk. Select NVIDIA

Now go to the [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) page and check is the driver listed in EnvyNG latest one. If it is, select automatic installation in EnvyNG and let it install the drivers. When it's done reboot the computer and thats all. To uninstall drivers via EnvyNG just select the option uninstall.

If the driver listed in EnvyNG is not the latest one you'll have to install it manually. First of all type:

```
sudo apt-get install build-essential libxft-dev
```

Next, download the latest driver from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) page and then in terminal (Alt+F2 and type gnome-terminal) type following (this will close graphical interface so read the HOWTO to the end first):

```
sudo /etc/init.d/gdm stop
```

If this closes the graphical interface but you can't write anything press ```
Alt+Ctrl+1
```. If graphical interface is not shut down reboot the computer and in grub menu select recovery mode (second option). When the new menu appears select Drop to root terminal.
When in terminal navigate to the location where you have downloaded nVidia driver ```
(for example if it's on your desktop type cd /home/username/Desktop/)
``` and start the installation by typing:

```
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
```

If your driver version differs from mine (173.14.12) write that name and not the above one. Installation is pretty straightforward and you can't do anything wrong. If you have problem with dependencies installer will tell you which packages to install. Simplest way to do it is to write the dependencies on piece of paper and boot to the graphical interface. Then start Synaptic ```
(Alt+F2 then gnome-terminal then sudo synaptic)
``` and search for the packages.

When installation is finished reboot the computer and thats all. Do not delete the driver as you might need it for eventuall uninstallation later.

To uninstall drivers that were installed manually close the graphical interface again (as when installing drivers manually), navigate to where it's located and type: 

```
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run --uninstall
```

Again, change the name of the file if you use some other driver version.

Good Luck
I tried My Best.

---

### Post by lynixus on 2011-02-15
WHOOW that's a really good HOWTO!
Thankyou alot!

---

### Post by Objekt on 2011-03-12
Recently I wanted to install the 260.19.44 drivers.

First thing I did was to uninstall the older 195.xx drivers that I had earlier installed using the Hardware Drivers applet.  So I did, and rebooted.  I logged in at the console so I could run the 260.19.44 Nvidia drivers package, which I had downloaded earlier.

The driver installer said it detected I already had some drivers installed.  260.19.44.  Same version I was trying to install.  How did that happen?

Also there were a BUNCH (I mean at least a dozen!) error messages during the install process.  I quickly lost track of what they were saying.  I kept hitting [Enter] hoping it would work anyway.

I guess it did, because I'm sitting here with the 260.19.44 drivers installed, with no problems so far.  But it seems weird that the installer thought I already had drivers installed, and all those error messages are Not Good either.

One side effect: the Nvidia X Server Settings applet (under System->Administration) is missing its icon.  I have no idea where to look for the icon, and I don't understand why it would be missing.

Another strange thing: The "Hardware Drivers" applet is now useless.  When I run it, it does not detect the Nvidia drivers I have installed, and does not offer the choice to install or uninstall older versions, as it always did before.  That can't be right, can it?

I think I broke something, and would like to know how to completely purge my system of all versions of the Nvidia drivers so I can start fresh.  Help?

---

### Post by linuxsyst on 2013-02-10
```
sudo apt-get remove purge nvidia*
```

---

### Post by wildmanne39 on 2013-02-10
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

