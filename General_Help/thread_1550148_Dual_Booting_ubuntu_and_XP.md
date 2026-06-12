---
title: "Dual Booting ubuntu and XP"
date: 2010-08-10
forum: General Help
---

### Post by technopersia on 2010-08-10
Hi, I had ubuntu installed first and I have just installed XP but the ubuntu doesn't load up.
Ive tried a few forum posts from the past but I can't get it working. Can anyone help me beginner style I don't know linux very well Ive only used it for a week (came to ubuntu thanks to windows being so bad, but still need it for softwares that wine can't handle)

Ive tried sudo grub but I receive a comandline error.
I have also tried this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
and received an error. (my partition was sda1) My partition containing ubuntu has also disapeared from the live USB!
Many Thanks in advance.

---

### Post by oldfred on 2010-08-10
Welcome to the forums.

Windows will install its boot loader into the MBR on windows install. You need to reinstall grub or grub2 to the MBR to get it to find Ubuntu.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

IF reinstall does not work download and run this from the liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by psycho5 on 2010-08-10
Hey, 

First thing, put in your live cd, let it boot up

go to Applications> Accessories > Terminal

find out where is your Ubuntu installed

sudo fdisk -l

Then, after finding out which disk it is, for example /dev/sda1, mount the it

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev

Go into that disk now as root

sudo chroot /mnt

Then install grub

grub-install /dev/sda

This will install grub on your disk. 

Unmount everything, then reboot. Your grub menu should be back up.

Boot into Ubuntu, then to add the XP option in your menu, just go into terminal again, and type:

sudo update-grub

it should automatically find XP and add an entry for it.

Good luck.

---

### Post by technopersia on 2010-08-12
Hi,

Thank you for the help Dual booting is now working. Special Thanks to psycho5!:popcorn:

---

### Post by technopersia on 2010-08-12
Hi, The dual booting worked a couple of times however everytime windows is about to load it restarts to the boot selection screen, Does anyone have any ideas how to overcome this?:confused:

---

### Post by oldfred on 2010-08-12
Post the results.txt from the bootinfo script in post #2.

---

