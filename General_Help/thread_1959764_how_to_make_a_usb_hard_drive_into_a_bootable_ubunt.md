---
title: "how to make a usb hard drive into a bootable ubuntu install?"
date: 2012-04-16
forum: General Help
---

### Post by sdowney717 on 2012-04-16
Can anyone share this info?
I have an IDE 320gb drive in a usb case and wanted to try it.

---

### Post by sdowney717 on 2012-04-16
tried the usb drive creator and got an error after it copied saying this
???

---

### Post by callmemahavir on 2012-04-16
Please look at the link...

[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

This URL will be very useful.

IT CONTAINS ALL THE INFORMATION!!!

---

### Post by sdowney717 on 2012-04-16
There is a bug in usb-creator-gtk
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/859539](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/859539)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/722019](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/722019)
run like this and it works
usb-creator-gtk --allow-system-internal


Perhaps I can boot the setup disk and install to the drive.
As this seems to give a max of 4gb

---

### Post by oldfred on 2012-04-16
You want a full install to the USB hard drive, but need a CD or USB flash drive to install to the USB hard drive. This all assumes your BIOS lets you boot from USB. Then your install is just like any install except you need to use manual install -Something Else to get the choice on where grub2 installs its boot loader. It normally defaults to sda, usually the internal and you want it on the external usually sdb.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")


For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by sdowney717 on 2012-04-16
Hi thanks that is it same idea.
How about just cloning what I got that would also give me a backup
Got some recommendations for that?
would also be nice if it could be fat32 so plugging it into a windows box I could view it all.
And also boot ubuntu

>  You can use it to** clone your Ubuntu 11.04 installation** that you carry along with you. And with the USB connection, you can use it on any computer that can boot off a USB device.


---

### Post by sdowney717 on 2012-04-16
the disk creator finishes now without error. likely only 4 gb available?

---

### Post by sdowney717 on 2012-04-16
rebooted and logged into this 
yes it is 4gb only.

I am also getting /cow error messages when I click on the drive icon in file manager

what is a cow?

---

### Post by sudodus on 2012-04-16
It is certainly possible to do what you want, and it can be made bootable by all computers that can boot from USB. Some computers identify it as USB, some identify it as (another) HDD. Check in the bios menu and select what is suitable for boot order and HDD disk order!

So select

- ***a 'standard' USB boot drive*** with the first partition for data available from linux and windows. So the second partition should be formatted as FAT32. The rest of the drive can be an extended partition with a casper-rw partition for persistence and a small swap partition. A partition can be larger than the 4 GB file size limit of FAT32. It is also more reliable. I use unetbootin to create bootable usb disks and pendrives, but there are many tools, that do about the same thing.

- ***a regular installed system*** (but installed to the USB drive instead of the internal drive). I would recommend such a system, because you can update and upgrade it without limits (except that it is slower than via IDE or SATA). It will be easier to install if you disconnect your internal drive during the installation. Furthermore, if you avoid proprietary drivers, it will be portable between computers. Also here you should make the first partition for data available from linux and windows. And the second partition should be formatted as ext4. Finally you can have a small swap partition.

So in both cases I suggest you install Ubuntu to the second partition.

If you search for other threads by me at the Ubuntu Forums, you will find some more details.

---

### Post by sudodus on 2012-04-16
> **sdowney717 said:**
> rebooted and logged into this 
yes it is 4gb only.

I am also getting /cow error messages when I click on the drive icon in file manager

what is a cow?
It's a big animal that says 'muuuu' ;-)

But in this case it is the device mounted on / (the root file system). It can be overlayed with the file system in the casper-rw file or partition for persistence. If there is no casper-rw, this file system is in RAM, so it is volatile (disappears at reboot or shutdown).

See the output of ```
df
```

---

