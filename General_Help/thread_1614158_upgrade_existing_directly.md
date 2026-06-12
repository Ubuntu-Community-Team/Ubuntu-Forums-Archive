---
title: "upgrade existing directly"
date: 2010-11-05
forum: General Help
---

### Post by csckid on 2010-11-05
I'm using ubuntu 8.10 which is already installed. Recently I have downloaded ISO file of ubuntu 10.04. Is there any way to install that ISO file i've downloaded without writing the ISO file in a CD?

---

### Post by celldweller1591 on 2010-11-05
You can do the installation via a bootable USB. If you want to upgrade your system, you have to download everything all over again. Update manager weill do that for you. For making USB bootable of ubuntu, use UNetBootin. google it. For details see [here]("http://www.linoob.com/forum/showthread.php?tid=93")

---

### Post by mrnelson1986 on 2010-11-05
If you want to upgrade your distribution, you can just enter in the terminal sudo apt-get dist-upgrade

This may not work 100% so PLEASE backup everything you have on your CPU that you want to keep, there may be incompatibilities between distributions.  You also may have to run it multiple times to go from 8.10 to 9.04 to 9.10 to 10.04, etc.

---

### Post by csckid on 2010-11-05
> **celldweller1591 said:**
> You can do the installation via a bootable USB. If you want to upgrade your system, you have to download everything all over again. Update manager weill do that for you. For making USB bootable of ubuntu, use UNetBootin. google it. For details see [here]("http://www.linoob.com/forum/showthread.php?tid=93")

What do you mean by "you have to download everything all over again"? do I need to download the ISO again? I don't want to download the file again. Downloading ubuntu takes me around 4 days. So upgrading using terminal is not a wise option for me. 

I read the article that celldweller1591 provided. I like the option b. Do I need to load the ISO file in my pendrive? can I change the bootable pendrive to normal once I have finished installing?

---

### Post by mrnelson1986 on 2010-11-24
Sorry I haven't checked back on this thread, it got lost in the shuffle.  If you are still wondering how to do this, there is no way that I personally know of to keep your system intact and upgrading manually with a 10.04 .iso from 8.10 or whatever you were at.  The only way to get to 10.04 is to either _download_ all of the updates using the script i posted earlier (sudo apt-get dist-upgrade).  Other than that, the only way to get 10.04 is to burn the .iso to a cd or USB drive, and fresh install from scratch (make sure you back up whatever you want to keep from the original 8.10 install) and then copy over the files from the backup you made.  Other than that, there is no way to do it manually just by upgrading what you have without the internet.

As for the link that celldweller posted, you just download the program to your current computer, plug the usb drive in, and run the program, pointing the install to the usb drive.  There is no reason to copy the .iso over manually to the drive, because it will be formatted when you do the install.  Once ubuntu is installed, you can format the drive again and revert it to normal, but it is nice to have a live usb copy around for troubleshooting :)

---

