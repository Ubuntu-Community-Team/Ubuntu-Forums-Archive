---
title: "Multiple Ubuntu's in GRUB"
date: 2011-09-01
forum: General Help
---

### Post by ksaul on 2011-09-01
I have been using ubuntu on my (dual boot) computer since 9.04, and every time I upgrade ubuntu, the grub appends a new option for ubuntu to boot to. So now I have a list of about 12 ubuntu optional boot's, and then my Windows 7 loader too... I would really like to trim this list down to only the NECESSARY ubuntu boot, and get rid of all the rest of them, how do I do this??

Also I am having trouble with 11.04 and booting into tty1 mode ([this thread]("http://ubuntuforums.org/showthread.php?t=1835761")) and I want to reinstall ubuntu completely, and do a fresh install of 11.04 instead of upgrading to it... so how do I successfully delete the partition table for ubuntu on my hard drive, so that I can freshly install 11.04 again?

The last time I uninstalled/deleted the partition table for ubuntu - it ****** up GRUB and my bootloader, and was unable to boot to anything (windows was all that was left) - and really do not want this to happen again...

---

### Post by xdominex on 2011-09-01
Old kernel versions are being kept around; uninstall all of your old linux images in synaptic package manager, then run the following in terminal and let me know if it solves your "multiple ubuntus in grub menu" problem:
```
sudo update-grub
```Hope this helps!

---

### Post by zero2xiii on 2011-09-01
Hay,

For "trimming" the grub menu, I suggest you install the program called "Grub customizer" [http://www.unixmen.com/software/1312-grub-customizer-20-released-with-a-user-interface-feature]("http://www.unixmen.com/software/1312-grub-customizer-20-released-with-a-user-interface-feature")

For a fresh install.. Just make sure during install where you must specify the partition, that windows is detected, then there shouldn't be any problems

:)

---

### Post by Frogs Hair on 2011-09-01
See the Ubuntu after Windows section at the link . If you are doing a clean installation and reformatting the portion of the drive currently  occupied by Ubuntu , Ubuntu , Grub , and all the old entries will be removed during the format  .[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by grahammechanical on 2011-09-01
Why do you think that you need to mess with the partition table in order to re-install Ubuntu?

I just boot from the live CD with the version of Ubuntu that I want and I choose Do Something Else. I then tell the installer the partition that I want Ubuntu installed in (by giving the partition the mount point of /) and mark that partition to be formatted. This wipes the old installation away (effectively).

I also give the old swap partition the mount point of /swap (otherwise a new swap partition will be created).

I have the home folder on its own partition, so I give it a mount point of /home BUT I **do not** mark it to be formatted - that way I do not loose my files and settings.

Regards.

---

