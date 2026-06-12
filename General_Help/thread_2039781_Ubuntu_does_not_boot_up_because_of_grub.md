---
title: "Ubuntu does not boot up because of grub"
date: 2012-08-09
forum: General Help
---

### Post by Zirts on 2012-08-09
So installed Ubuntu on some old machine today and it appears that after the installation, Ubuntu will not boot up. 

I can only boot it up when I insert the USB stick I used to install it with and put THAT to boot first device not the harddrive ubuntu was installed on.

Any ideas on how to fix it?

(When I made system updates in Ubuntu it at somepoint gave a grub error also and sayd that I should relocate on what drive grub should be on and that if i am not sure I should check all the drives, I did so and clicked forward but then it gave me an error again that grub failed to do it.)


Any ideas on how to fix this?   Always booting from USB stick from now on seems a bit stupid...

---

### Post by Zirts on 2012-08-09
I allready read from somewhere to start up Ubuntu from USB stick as live-USB, but I dont see how I can do it as when I bootfirst the USB stick on which I have the Ubuntu boot install on, it just instantly starts up the Ubuntu on my hard drive.

---

### Post by oldfred on 2012-08-09
You just need to reinstall grub2's boot loader to the MBR of the internal drive. Some computers promote the USB drive to sda when installing and grub defaults to installing into sda.

You can just boot and run this, but grub has saved an entry also.

sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub


#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

