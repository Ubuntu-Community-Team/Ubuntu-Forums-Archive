---
title: "Live ISO for Multiple Ubuntu Variants?"
date: 2011-05-17
forum: General Help
---

### Post by kuloch on 2011-05-17
I have recently been playing with [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") to create a USB flash drive with several live image Linux distros.  After setting it up with Ubuntu, Kubuntu, Xubuntu, and Lubuntu, I started wondering whether there exists a single ISO with all (or multiple) of the Ubuntu variants.  I have about 2.7 GB taken up with each of those four ~700 MB ISOs, and I figure there has to be quite a bit of duplicated code there (please correct me if I'm wrong).  I'd also like to have Ubuntu Studio's tools included, and they don't provide a live CD/DVD image.

Would [Remastersys]("http://geekconnection.org/remastersys/") be my best option for creating such an ISO?  Presumably (just read about it tonight), I would install a fresh copy of Ubuntu, install the appropriate packages with Synaptic, create the image, and load it onto the USB drive.  I'm game for doing that, but I suspect that someone out there must have done the same thing before and made it publicly available.  Does this already exist?  I would very much appreciate any leads.

A couple years ago I had a Ubuntu/Kubuntu/Xubuntu setup, trying to decide which I liked best at the time.  Would anyone mind reminding me whether such a setup yields the same UI look-and-feel as if only the appropriate variant had been installed?  E.g., does Ubuntu with the kubuntu-desktop package installed act exactly like a Kubuntu install after logging in with KDE selected?

As sort of a side note, I've had to do quite a bit of playing around with things to get this  [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") setup to work with the Linux Mint 11 RC and BackTrack 5.  Conveniently, their single [USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") has both - which allowed me to create them on a separate flash drive, copy the files into unique folders on the YUMI drive, create menu entries, and play with each distro's kernel append options until they would actually boot.

While searching around regarding this post's original question, I came across [UNetbootin]("http://unetbootin.sourceforge.net/"), which sounds like it might be more generically usable than the [PenDriveLinux]("http://www.pendrivelinux.com") tools I've been using.  Does anyone know whether it can be used to boot multiple images like [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/")?  Or is it a one-image-per-drive deal?

---

### Post by kuloch on 2011-05-17
bumping this up from page 15

---

### Post by gene simmons on 2011-05-18
i use netbootin and it only does one iso at a time,i searched the net and found multisystems and its a wicked program,i loaded 5 isos and they all worked except google chrome os.not sure why it didnt,it does alot more than boot isos,u can sync it to virtualbox and test ur isos before putting them on the  usb stick,works great:guitar:

---

### Post by oldfred on 2011-05-18
I did this manually before I found these scripts:

USB:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

CD:
multicd.sh - combine Linux ISOS into one CD
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
CD/DVD multiboot
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

Manually create USB:
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

Hard Drive:
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by kuloch on 2011-05-24
Thanks for the info on USB booting.  I'll definitely look into those further, as it would be *really* convenient to be able to use just the .iso images for each distro.

Anyone have any input on an existing *buntu compilation image?  Or will I need to make it myself?

---

### Post by oldfred on 2011-05-24
I installed kde with my Ubuntu, but decided I did not like it several versions ago. But I could not just uninstall as I do like K3b and KMyMoney. It left bits and pieces everywhere. I now prefer just to use another 20GB root partition and do a full install. 

The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo service gdm start

---

