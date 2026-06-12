---
title: "grub bootloading problems"
date: 2011-07-03
forum: General Help
---

### Post by uptown_mo on 2011-07-03
hi, this is my first post in this forum but i have been reading for quite awhile.. here is my situation.. i have ubuntu netbook remix 10.10 installed to my netbook harddrive.. i was installing debian squeeze to a usb drive and when asked about installing grub i said yes by accident..it installed grub and now i cannot logon to ubuntu.. i do not have a live cd...
my questions:

how do i remove the grub menu and boot directly to ubuntu on my harddrive?

how do i then make my usb drive with debian installed bootable?

thanks everyone for all the support

---

### Post by oldfred on 2011-07-03
Welcome to the forums.

I think you just need to install Debian's grub boot loader to the USB drive's MBR and install Ubuntu's grub2 boot loader to the MBR to the internal drive.

Does not Debian use grub2? Does it include the os-prober? I might try installing it if it does not (do not know for sure) and see if this finds Ubuntu.

sudo update-grub

To reinstall grub from Debian to sdb.

I think everything should be the same for Debian but am not positive:
#reinstall from working (not liveCD) system - first find external drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
[COLOR=Red]sudo grub-install /dev/sdb[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If you cannot get Debian to find Ubuntu you can reinstall with a liveCD or liveUSB. You should use same version of Ubuntu as you have installed.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

There are some ways to manually boot if you can boot to a grub menu in one but then use grub's command line to specify another system.
Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by uptown_mo on 2011-07-03
wow, really couldn't have asked for more, thanks... let me give it a try and will post back with results...

---

### Post by uptown_mo on 2011-07-03
solved

for debian i used the installer usb and on the install menu i chose install grub menu to my usb drive...no problems works perfect.

for ubuntu i updated the MBR as posted..(thanks)

the answer is yes Debian installs using the grub2 bootlader...

---

