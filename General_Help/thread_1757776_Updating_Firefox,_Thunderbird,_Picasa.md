---
title: "Updating Firefox, Thunderbird, Picasa"
date: 2011-05-13
forum: General Help
---

### Post by newairly on 2011-05-13
First, I am a newcomer to Linux.

I have just got an Asus eeepc900 with Easy Peasy 1.6 (Ubuntu 10.04)
I can find no way to update  Firefox, Thunderbird, Picasa. The option in the menus are either missing, or greyed out. I have enabled automatic updates, with confirmation required, but nothing seems to have happened.
Firefox is 3.6.3  Picasa is 3.0.0 beta These came with the Easy Peasy distribution. Thunderbird is newly installed.

How do I go about getting later versions without completely uninstalling first!

Also, how can I get rid of unwanted files to make more disk space? Is there an automatic "clean up" available? I seem to have suddenly lost about 500MB from the 4GB partition where the OS is installed.


Thanks, Phil

---

### Post by Dave_L on 2011-05-13
On Linux, applications are normally installed and updated with a package manager.  On Ubuntu and other Debian-based distributions, the basic package manager is "dpkg", which can be used directly or through various front-ends, such as "apt-get", "synaptic", "aptitude", and "Update Manager". My preference is "synaptic", which should be accessible through System >> Administration >> Synaptic Package Manager.

Assuming Firefox, Thunderbird and Picasa were installed through the package manager, they can be easily updated the same way.

---

### Post by lovinglinux on 2011-05-13
In Linux, softwares are updated via repositories, that's why the built-in update managers of those applications are grayed out.

To update them,  go to "System >> Administration >> Update Manager".

Personally, I prefer to do things via terminal. You can upgrade your applications with the following commands:

```
sudo apt-get update
sudo apt-get upgrade
```

If you are looking to update to Firefox 4, then keep in mind that Ubuntu only provide security updates. Your version of Ubuntu runs Firefox 3.6.x. If you want the latest Firefox, you will need to upgrade Ubuntu to a new version or get the software from other repositories. See the [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for instructions. I strongly recommend Firefox 4.

For file cleanup, install BleachBit.

---

### Post by newairly on 2011-05-15
Thanks for that info. I have installed Bleachbit and it recovered 200MB but I still seem to be missing 2-300MB that I had shortly after installation of Easy Peasy and then Thunderbird. I did install a package to manage the touchpad, but removed it again. The space seemed to disappear about then. I have only 350MB free on the 4GB SSD system disk and Picasa complains that it wants more. I have my user files on the 16GB SSD
I have turned off automatic upgrades because I do not know if they will use up even more space.

As you can see I am a real newcomer. My last experience with Unix was about 20 years ago.

Phil

---

### Post by Dave_L on 2011-05-15
This can help identify what's taking up the space:
Applications >> Accessories >> Disk Usage Analyzer

---

### Post by mikewhatever on 2011-05-15
I suspect that while EasyPeasy may be based on 10.04, it doesn't use the official repositories. Foe example, the latest version of Firefox in 10.04 is 3.6.18. You may want to look at the list of sources:
```
less /etc/apt/sources.list
```

As for clearing up some space, uninstall applications that you don't need, empty Trash, delete cached installation packages, remove older kernels:
```

sudo apt-get clean
sudo apt-get autoremove
dpkg -l | grep linux-image
```

---

