---
title: "Ubuntu 10.04 on USB Stick - Persistence Feature"
date: 2010-06-18
forum: General Help
---

### Post by KAWill70 on 2010-06-18
The Pendrive Linux site states the following in regards to a USB Flash Install using their Universal USB Installer:

"Once finished, you should have a Live USB Ubuntu 10.0 that can be run directly from your Flash Drive, just as it does from a Live CD. Ubuntu's  casper-rw feature **IS ALSO** utilized for persistently saving and restoring your changes on subsequent boots."

The part that confuses me is the second statement that the Casper-RW feature is utilized.  Isn't that incorrect for the case of a Live Install using their Universal USB Installer?

I later discovered that a Persistent Install can be created by downloading and using Version 2.5 of the Linux Live USB Creator.  In this case, a second partition is created on the Flash drive for the casper rw feature.

Is my understanding correct, or can the Pendrive Linux Universal Installer somehow create a persistent USB drive that will save data and settings?

Thanks, Kent

---

### Post by nemiux on 2010-06-18
Well, I'd personnaly recommend using uNetbootin or usb startup disc creator which is in System-->Administration(as i remember cause im not on ubuntu now). Yes, it's possible to have ubuntu on a flash drive and use it, and save data, soft you've downloaded and so on. However, you can also install it. When loaded to ubuntu screen you see an icon on desktop install, which is used to install ubuntu to hdd.

P.S. If Ubuntu usb startup disc creator that is in system tab is used, when you boot you should see an option to install, without any need to load the system itself

---

### Post by wilee-nilee on 2010-06-18
> **KAWill70 said:**
> The Pendrive Linux site states the following in regards to a USB Flash Install using their Universal USB Installer:

"Once finished, you should have a Live USB Ubuntu 10.0 that can be run directly from your Flash Drive, just as it does from a Live CD. Ubuntu's  casper-rw feature **IS ALSO** utilized for persistently saving and restoring your changes on subsequent boots."

The part that confuses me is the second statement that the Casper-RW feature is utilized.  Isn't that incorrect for the case of a Live Install using their Universal USB Installer?

I later discovered that a Persistent Install can be created by downloading and using Version 2.5 of the Linux Live USB Creator.  In this case, a second partition is created on the Flash drive for the casper rw feature.

Is my understanding correct, or can the Pendrive Linux Universal Installer somehow create a persistent USB drive that will save data and settings?

Thanks, Kent

If you create a loaded usb with persistence the casper-rw is in home. If you want to have a larger then 4 gig size for this check out this link.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

Unetbootin doesn't provide persistence, there may a work around though, but I have never myself been able to create a persistence with a second ext2 partition named casper-rw with unetbootin

With a ISO loaded thumb though there are limitations for what you can do as the ISO is the default and kernel updates and distro upgrades are not encouraged.

If the thumb is big enough say 8 gigs a full install will be a good way to go, just make sure grub is put in the mbr of the thumb. This does have limitations as well in being able to boot it on any computer, but I have a 16 gig loaded this way and it boots on 3 of my computers with no problems.

---

### Post by C.S.Cameron on 2010-06-18
You can have both casper-rw persistence files and partitions.
You can also have home-rw persistence files and partitions.
The second will save home folder stuff.
The first will save downloaded programs and if there is no home-rw it will save home folder stuff also.

Any of the Live CD disk image installs and even the Live iso boot disks will try to find the closest file or partition named casper-rw and home-rw to save stuff to, When the persistence option is selected.

(Even the Live CD will look for these partitions)

---

### Post by wilee-nilee on 2010-06-18
> **C.S.Cameron said:**
> You can have both casper-rw persistence files and partitions.
You can also have home-rw persistence files and partitions.
The second will save home folder stuff.
The first will save downloaded programs and if there is no home-rw it will save home folder stuff also.

Any of the Live CD disk image installs and even the Live iso boot disks will try to find the closest file or partition named casper-rw and home-rw to save stuff to, When the persistence option is selected.

(Even the Live CD will look for these partitions)

I had not thought about home-rw thanks.

---

### Post by C.S.Cameron on 2010-06-18
Casper-rw does generally not work after upgrading from one version to another. 
With a home-rw file or partition all your home folder stuff can be recovered.


edit:
> I had not thought about home-rw thanks.
You can take a fresh casper-rw file change the name to home-rw and stick it back in the root of the persistent flash drive install.

---

### Post by wilee-nilee on 2010-06-18
> **C.S.Cameron said:**
> Casper-rw does generally not work after upgrading from one version to another. 
With a home-rw file or partition all your home folder stuff can be recovered.


edit:

You can take a fresh casper-rw file change the name to home-rw and stick it back in the root of the persistent flash drive install.

That is more good info thanks. I generally only use the ISO loaded thumbs for installs. Thats why I bought a 16 gig for full installs.:p

---

### Post by KAWill70 on 2010-06-19
[B]Thanks all for your replies.

All information provided is a great help and I need to review each note carefully.

I forgot to enable email notification and just discovered the lengthy thread.[/B]

---

### Post by dcstar on 2010-06-19
Be aware that the Persistence feature (still?) uses the SquashFS which means that you progressively lose filespace because once it is taken, it is never returned.

What this means in practice is that your Persistent free space will just get smaller and smaller even if you delete files, and one day you will have to wipe it out and recreate it to return to something you can actually store data on.

I have seen HOWTOs on creating custom Live USB setups that use a normal filesystem, but these are horribly complicated.

---

### Post by KAWill70 on 2010-06-19
> **dcstar said:**
> Be aware that the Persistence feature (still?) uses the SquashFS which means that you progressively lose filespace because once it is taken, it is never returned.

That sounds similar to the way Thunderbird stores email, although in the case of Thunderbird one can recover file space by Compacting Folders.

The link below shows how Pendrivelinux installs Ubuntu 10.04 on a Flash Drive.

[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

They provide a link for downloading their Universal USB Installer.

The Installer does indeed offer a Persistence Feature on the Flash Installation and I apparently did not notice it initially.  One can select No Persistence plus several options starting with 1GB Casper RW.  My Flash Drive is up and running and appears identical to the version I made earlier with the Linux Live USB Creator.

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Both of these tools are a huge improvement over what was available previously.  I installed Knoppix and Ubuntu on Flash drives using a complicated manual process that was also somewhat risky.  If one entered a wrong disk drive letter they would format their Windows disk drive.  These tools seem to have eliminated that risk and made the entire process very easy.

---

