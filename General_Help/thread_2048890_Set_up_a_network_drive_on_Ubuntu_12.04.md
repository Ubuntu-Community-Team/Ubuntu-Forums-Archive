---
title: "Set up a network drive on Ubuntu 12.04"
date: 2012-08-27
forum: General Help
---

### Post by dupondd on 2012-08-27
Hello,

I would like to set up a network drive (file system : NTFS) on my ubuntu account, but I don't know how to do it easily.

We can access it easily under Windows thanks at this address "\\TEST" .
Please not that there is an id and password requested. Also I would not like to mount this by hand everytime I reboot.


I tried this tutorial : [http://www.liberiangeek.net/2012/04/auto-mount-windows-ntfs-partitions-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/auto-mount-windows-ntfs-partitions-in-ubuntu-12-04-precise-pangolin/).
 I don't know why, but blkid returns me only ext4 and swap type but nothing like ntfs. I guess it shows only the machine parts, but not the network.

Thank you in advance for your help

---

### Post by LewisTM on 2012-08-27
On a network, clients are oblivious to the file system (e.g. NTFS, FAT, Ext4, XFS, etc.) underlying shares. You have to setup you Ubuntu client to access CIFS a.k.a Samba a.k.a Windows shares, not physical drives.

Can you see your network share in Nautilus's Network section? If so, you can start from there and setup an automatic connection with Gigolo ([FONT="Courier New"]sudo apt-get gigolo[/FONT]), if desired, or go with [automatic mounting]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") of a CIFS share at the system level by editing /etc/fstab.

Cheers!

---

