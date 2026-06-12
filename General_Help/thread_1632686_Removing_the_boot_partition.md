---
title: "Removing the boot partition"
date: 2010-11-28
forum: General Help
---

### Post by sid.ambi on 2010-11-28
I have only Ubuntu 10.10 on my system. I made a separate partition for /boot folder (/dev/sda1/) which is 100 MB in size. Now I want to install windows 7 on my computer, I wish to convert this partition to the system reserved partition in windows.

I googled a bit for the problem & found exactly opposite process (in [*_ubuntu documentation_*]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall")), where one can create a new /boot partition after installation. I wanted to know whether it is safe to use the same process for removing that /boot folder. Or is there a method for making a new /boot folder using the Live CD/USB?

---

### Post by dino99 on 2010-11-28
standard ubuntu installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sid.ambi on 2010-11-28
Hey Dino99,
I did not understand what you wrote.
BTW I don't want to reinstall because I have installed many applications on my system...

---

### Post by oldfred on 2010-11-28
If you create the NTFS primary partition (with boot flag) in advance win7 will install to just the one partition. It normally creates the boot/recovery partition on new installs, so you can encrypt the main install if desired, but is not required.

I just moved the files in /boot to a boot partition then decided I really wanted a /grub partition and moved the files back (that was with old grub but it is the same). You need to move everything in /boot into the /boot folder in your root partition and reinstall grub so it now sees the new location of all the kernels & grub files in /boot and sudo update-grub. Use cp with -a or rsync to preserve permissions & ownership (should be root anyway)

---

### Post by sid.ambi on 2010-12-09
I installed windows without creating a separate partition for the system reserved space.
Thanks for your help.

---

