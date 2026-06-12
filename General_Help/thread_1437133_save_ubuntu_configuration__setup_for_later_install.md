---
title: "save ubuntu configuration / setup for later install"
date: 2010-03-23
forum: General Help
---

### Post by panti19 on 2010-03-23
Hi, I run ubuntu 9.10 and i've set up my drivers/music player/themes/browser etc just the way i like them.
However I now want to install XP and dual-boot.
My hard drive is not partitoned, so I want to ask if there is a way to save my setup to use after installing XP.

thanks

---

### Post by ajgreeny on 2010-03-23
You just need to use gparted on a live CD to make either some free space, or an ntfs partition into which you install XP, then restore grub, then, if it's grub2 on ubuntu 9.10, just boot into ubuntu and run sudo update-grub to let it find and add windows to the grub menu.

By all means backup your files, or use clonezilla if you wish to clone your current setup, but installing XP will not damage your present OS if you do as I say above, it will simply take some of the space from it.

Alternatively, you could just run XP in a virtual machine such as VirtualBox, but use the PUEL version from Sun direct, not the open source version from the repos, as Sun's has several advantages over the OS version.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by eksasol on 2010-03-23
-Boot into Ubuntu Live CD and run GParted. Resize your Ubuntu partition to make room for XP.

-Create a second partition which will be the XP partition, format it as NTFS. Right click on it and choose "Manage Flags", then check "boot". You need to do this so when you install XP, it will see this new NTFS partition as the C: drive. Otherwise, it will be detected as D: and you don't want that.

-After you installed XP, boot the Live CD and run GParted again. This time, "Manage Flags" on your Ubuntu partition and check "boot". This will tell the computer to boot into your Ubuntu partition when turned on, instead of XP.

-"If" while botting into Ubuntu andGRUB is no longer found, its because XP may have wiped out the MBR data that contains GRUB boot. To fix this, boot into the Ubuntu Live CD and restore GRUB using these instructions: [Grub 2 via LiveCD](https://wiki.ubuntu.com/Grub2#Recover)

Recommendation: The next time you install Ubuntu, when it ask for what partition to install to, choose the manual option. Then create a partition for Ubuntu to install to and mount it as "/". Create another partition and mount it as "/home". This way, even if you have to delete the partition that contain the Ubuntu operating system, your user profile is still saved in a separate partition.

---

### Post by colorlessprism on 2010-03-23
my personal favorite is remastersys: 
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
it is very easy to use and actually creates a live CD based on your configuration; even copies settings and such. one thing you may have to do is comment out your big folders (for me Documents, Music, Pictures, Videos, and .wine) and back them up on to a flash drive. remastersys really makes it easy to experiment with things as if i screw anything up i can go back to my old install in a matter of minutes...

oohh if you use remastersys you will also need:
A) "USB startup disc creator (should be repositories) and at least a 4gb flash drive
B) a DVD-R and Brasero or your favorite iso burning capable software (i havent burnt a CD/DVD in a very long time, so i cant even tell you whats current)

---

### Post by panti19 on 2010-03-23
thanks for the replies.

i went for virtual machine for the ease of use and successfully installed xp inside ubuntu.

however i noticed that even if i gave it 1GB of RAM and 10GB of disk space, the system is a tad slow. I want to use it for an audio mixing program which i bought for windows (Acoustica Mixcraft) and 3d (Sketchup, AutoCAD, ArhiCAD, 3dMax). 

did i make the right choice here? thanks

---

### Post by eksasol on 2010-03-24
> **panti19 said:**
> thanks for the replies.

i went for virtual machine for the ease of use and successfully installed xp inside ubuntu.

however i noticed that even if i gave it 1GB of RAM and 10GB of disk space, the system is a tad slow. I want to use it for an audio mixing program which i bought for windows (Acoustica Mixcraft) and 3d (Sketchup, AutoCAD, ArhiCAD, 3dMax). 

did i make the right choice here? thanks You'll have to install VirtualBox Additions. When you run XP, click on Devices in the menu on the top and choose "Install Guest Additions". However, before that you have to go Virtualbox main menu, choose "Setting" on your virtual XP, go to Display tab, enabled both 3D and 2D acceleration.

No.. bad choice with Virtualbox for audio production and 3D editing. It have very poor support of 3D graphic, I doubt your 3D program will even run. An alternative for 3D in virtual machine would be VMWare, which have better support. VMWare Player is a free version, but I had extreme problems running it in Ubuntu and it couldn't even run properly.

As for audio mixing, the sound card inside the virtual machine is ...virtual. There are some good audio software for linux though I am not expert in this field. Audacity for wave editing, Hydrogen for drum, Jokosher which is similar to Garageband, LMMS is a DAW, you can search around.

Audio mixing should be possible, but for CAD it's better that you follow my steps and dual boot.

---

