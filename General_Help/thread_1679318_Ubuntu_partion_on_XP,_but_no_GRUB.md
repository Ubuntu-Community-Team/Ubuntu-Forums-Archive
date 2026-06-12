---
title: "Ubuntu partion on XP, but no GRUB"
date: 2011-01-31
forum: General Help
---

### Post by BlackLab on 2011-01-31
Hi all,
I never got around to installing Ubuntu on my Netbook. I did not wish to potentially mess up the boot process for Windows as I am not the main user of this Netbook. 

I can install Ubuntu on a partition next to Windows .. but I don't want to disturb the Boot sector for C: windows.

Where can I put GRUB? It occurs to me I could put GRUB onto a pen drive, as only when I insert the pen drive will GRUB give me the option to boot to Ubuntu on the HDD.

Will this work? Is there a better way?

cheers

---

### Post by khamil8686 on 2011-01-31
id just install grub over the boot sector of windows and then set windows to be the default os to boot and set the GRUB_TIMEOUT to be 1 so if you want to boot into ubuntu you just watch for the screen to pop up to select ubuntu, it will add 1 second to the boot up time but tons of people dual boot linux and windows without problems :) if windows got reinstalled you would have to reinstall grub but thats the only problems i can really forsee

---

### Post by BlackLab on 2011-01-31
Thanks for the quick reply.
I have considered carefully the option to overwrite the windows boot sector , but I read a few too many boot problems here. For example there is one in this forum section where the subject line is something like GRUB can't find Vista. Also I read that when GRUB is updated via Ubuntu auto updates .. there might be some unseen difficulty .. maybe there is not such a high probability for these problems, as many dual boot with no problems as you rightly point out... but I never want to risk a problem with booting to Windows ... (more than my life is worth :))

---

### Post by khamil8686 on 2011-02-01
to avoid it at all costs id install grub to a usb drive and then whenever you want to boot into ubuntu just insert the usb stick and  tell the bios to boot from it before booting the normal hard drive,  heres a link on a tutorial how to install grub2 to usb :) [http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)
hope it helps! post back with problems :)

here is a thread on installing grub2 to usb
[http://ubuntuforums.org/showthread.php?t=1515343](http://ubuntuforums.org/showthread.php?t=1515343)

the first tutorial seems more complicated and im not sure if it would automatically detect all partitions on your computer or if you would have to enter commands to boot one manually, the second one has a line of code to run in a terminal that i believe would install it in one swipe and also detect all your existing partitions automatically and create a boot list for you with
```
sudo grub-install --root-directory=/media/USBFolderName /dev/sdx
```
where /dev/sdx is the block device of the mounted usb drive
im not sure if grub-install is the same for installing grub2, if the above code doesnt work you could try grub2-install instead
most commands i see of grub2 just add the 2 onto original grub commands, ex: sudo update-grub is now sudo update-grub2 but i believe sudo update-grub is a symbolic link to sudo update-grub2 if you have grub2 installed

---

### Post by Mark Phelps on 2011-02-01
> **BlackLab said:**
> Hi all,
I never got around to installing Ubuntu on my Netbook. I did not wish to potentially mess up the boot process for Windows as I am not the main user of this Netbook. 
Then maybe ... since it's not yours, you should leave it alone!

> I can install Ubuntu on a partition next to Windows .. but I don't want to disturb the Boot sector for C: windows.
And if you hose that up in any way, since the netbook probably can not boot from CD, how exactly are you going to fix up the mess?

>  Where can I put GRUB? It occurs to me I could put GRUB onto a pen drive, as only when I insert the pen drive will GRUB give me the option to boot to Ubuntu on the HDD.
IF you install Ubuntu to a USB drive, GRUB will almost certainly get installed (by default) to the "first" drive it sees -- the internal drive that you don't want overwritten!  So basically, unless you are VERY CAREFUL, you will mess up this netbook -- something the "main user" will most certainly NOT appreciate.

> Is there a better way? 

Yeah -- go buy your own netbook and experiment with it.

IF it was MY netbook and I was kind enough to let you use it, I would certainly NOT want you experimenting with it -- in ways that could hose it up.

---

### Post by Rubi1200 on 2011-02-01
Rather than messing up a computer that is not yours, why not install Ubuntu on a flash drive with persistence so you can save files and settings?

There are plenty of tutorials out there:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by BlackLab on 2011-02-01
Thanks for the advice .. I think I'm good to go on this .. I'm fairly sure that when I installed Ubuntu on my external HDD, the installation program asked where I would like to install GRUB. So I think .. as long as I have the pen drive inserted when I install Ubuntu to a new partition on the Netbook's HDD it will offer to install GRUB on it (the pen drive).

First thing I will do though is make an image of the Netbook's HDD on my external HDD. That way if it all goes wrong I can restore the image (naturally including XP) to the Netbook.

cheers

---

