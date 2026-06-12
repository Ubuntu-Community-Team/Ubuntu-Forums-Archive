---
title: "Installing ubuntu 9.10 without the disc"
date: 2010-05-08
forum: General Help
---

### Post by Lakeside5 on 2010-05-08
I have to do a complete reinstall of Ubuntu 9.10 (wipe my system and reinstall) and I have a problem.  My disc drive doesn't work, it only shows the files in the disc, but I can't boot from it, so the ubuntu boot disc for 9.10 is useless. I was also told I could use an external hard drive which I have, but it is full of backed up files (like all my kid's pictures) and I was told that the ex. HD had to be blank, only the Ubuntu distro on it, to work.  I don't want to take all my files off of it.  Is there any other way, like can I just download the distro into my HD, then run it? thanks.

---

### Post by -humanaut- on 2010-05-08
You can install off a USB drive. If you want you could try a PXE install I'd have to dig up the directions on the install for it though if you wanted to go that route.

---

### Post by Lakeside5 on 2010-05-08
Sorry to be so dense (lol) but by usb, you mean I could just use a memory stick (and what size memory stick?).  So I would download the disro files..from somewhere, onto the memory stick, and boot from there?  Thanks.

---

### Post by oldfred on 2010-05-08
grub2 will loop mount the iso and let you start it but you can only install to unmounted parititons. If your install is a logical all the logicals in the extended partition are logically (not actually) mounted since the extended is mounted. If you have it in a primary and want to install to a logical it should work.

Several of the USB installs want to erase the USB flashdrives. I have a USB install that just uses a grub partition, has grub in the MBR and loop mounts several ISOs. the ISO only may require only 1GB. I am using a 4gb flash but have 5 or 6 ISOs on it.

You can do a full minimal install from your primary to your secondary drive and then reverse the procedure.  If you have about 4GB on your data drive it should work. Again you should have good backups for any system changes.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

---

