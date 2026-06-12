---
title: "Installing Nvidia driver"
date: 2010-06-07
forum: General Help
---

### Post by charan315 on 2010-06-07
when i am trying to install nvidia driver shows error:

You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com]("http://www.nvidia.com").


how to exit the x server?
using Ubuntu v10.04.

---

### Post by Breambutt on 2010-06-07
I suggest you take a look at Main Menu > System > Administration > Hardware Drivers.

Much more foolproof than doing it that way with limited experience.

For future reference, ctrl+alt+F1 for console, log in as usual and terminate X with *sudo service gdm stop* (and *start* to relaunch). But I digress, I strongly suggest avoiding this and there's also no need to install NVIDIA drivers manually in Ubuntu.

---

### Post by gastly on 2010-06-07
I agree with Breambutt, what he suggested is the most safe way to install the drivers, but in case you ever want to install the drivers downloaded from nvidia's site, do this:

First install the linux kernel headers for your kernel:
```
sudo apt-get install linux-headers-`uname -r`
```

Then follow these steps:

**1.** Press Ctrl+Alt+F2 , This will take you to a console login promt, enter your username and password.

**2.** Stop the X server

```

## For GDM (Gnome)
sudo service gdm stop

## For KDM (KDE)
sudo service kdm stop

```

**2.** Navigate to the directory where you downloaded the Nvidia driver file, I'll assume you downloaded to $HOME/Downloads.

```
 cd ~/Downloads 
```

**3.** Install the drivers using this command:

```
sudo sh ./NVIDIA-filename
```

[color=blue]Note: Replace the 'NVIDIA-filename' with the name of the driver file you downloaded[/color]

**4.**Start X again

```

## For GDM (Gnome)
sudo service gdm start

## For KDM (KDE)
sudo service kdm start

```

And that's it :)

---

### Post by charan315 on 2010-06-17
**1.** Press Ctrl+Alt+F2 , This will take you to a console login promt, enter your username and password.

when i am entering the correct the login (admin or user) it shows error, and after some time shows battery status OK and hangs.

---

