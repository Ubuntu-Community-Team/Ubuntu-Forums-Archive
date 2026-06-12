---
title: "Move Ubuntu from Virtual machine to physical PC"
date: 2011-07-10
forum: General Help
---

### Post by adrianhb on 2011-07-10
Hi everyone,

Thought I'd write a tutorial on moving a Ubuntu install from a virtual machine to a physical machine as I have had to do just this and was unable to find any definitive tutorial on the procedure, there are many for the opposite or backing up to the same machine. This is my first ever Linux Tutorial so if it is a little disjointed I apologise.

I have taken bits and pieces from various tutorials and thank those people who have taken the time to help people like me who's Linux knowledge could be written on the back of a postage stamp. This is my little bit and I hope it proves helpful to others, I am fairly certain that this could be used to move between all hardware/software installations.

Ok first thing to do is back up the virtual machine to a zip file. Unlike Windows you have full access to files in Linux even if they are in use, you are also able to simply copy the directory structure from one machine to another.

Open a terminal session if you are using the Desktop version or run from the command line for the server version

In order to have full access and permissions you need to be the root/Super user

```
sudo su
```next thing to do is create a location to backup the system to there are a couple of options, back up locally or to external media like a usb drive personally i backed up straight to the usb as it meant i didn't have to copy it to the usb later

to backup to the HDD you need to have a location that will not be included in the backup file, we will be excluding /media from the backup so create a folder within the /media folder

```
mkdir /media/backup
```if you wish to backup directly to the USB you first need to mount the USB drive.
before you plug in the USB drive run the following:

```
ls /dev
```make a note of the directories listed and then plug the usb drive into the machine and after a few seconds text should appear showing the USB has been loaded then run the ls /dev again

there will be a couple of extra entries usually sdb and sdb1

you now need to create a mount point for the USB drive

```
mkdir /mnt/usb
```now mount the USB to the newly created folder

```
mount -t auto /dev/sdb1 /mnt/usb
```you should be able to see the contents of the USB by running

```
ls /mnt/usb
```Ok now to do the backup

for backup to the HDD

```
tar cvpzf /media/backup/UbuntuPC.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/dev --exclude=/boot /
```for backup to the USB

```
tar cvpzf /mnt/usb/UbuntuPC.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/dev --exclude=/boot /
```this will take 15-30 mins to complete, in this time you can prepare the physical machine

You need to make sure you have the same install version CD as the system you are moving from the virtual machine

On the new machine run the install and do a bare-bone install with no extra options, anything you added at install of the original machine will be added to the new machine when you restore the backup files

once the install has completed you will need to backup a file called fstab, the best thing is to back it up to the /media/backup folder, see the above instructions for creating this folder on the new machine then become the root/super user

```
sudo su
```then run

```
cp /etc/fstab /media/backup
```Back to the virtual machine...

once the backup procedure is complete in the virtual machine you will need to get it onto the new PC, if you backed up directly to the USB you simply have to unmount the USB and put it in the new machine

```
umount /mnt/usb
```remove the USB device

if you backed up to the HDD you need to copy the file to a removable drive like a USB key, see the above instructions for mounting USB then run

```
cp /media/backup/UbuntuPC.tgz /mnt/usb
```unmont the USB, remove and plug the usb into the new machine, once detected mount to /mnt/usb using the instructions above

now you simply have to unpack the backup file to the root folder

```
tar xvpzf /mnt/usb/UbuntuPC.tgz -C /
```this should only take a few mins

as we did not include /dev and /boot in the archive the hardware layer for the new machine should work but the fstab file we backed up earlier needs to be put back as the one from the virtual machine will cause problems on reboot

```
cp /media/backup/fstab /etc
```there is one last issue that needs to be sorted, the network card, you need to delete a file so that Ubuntu will rebuild the network layer on reboot

```
rm /etc/udev/rules.d/70-persistent-net.rules
```now reboot the machine and you should have your old virtual Linux machine running on the new hardware

---

### Post by C.S.Cameron on 2011-07-10
Job well done.

---

### Post by gizmo720 on 2011-07-10
Can't you just copy the entire filestructure over, then install grub on the new system?

---

### Post by wildmanne39 on 2011-07-11
Hi, coping virtual machines only work if you are changing like file locations on the virtual machine and you have not saved any snapshots, so it is a very bad way to try. It changes the uuid of the drives if I remember correctly. There is a guide for doing it at the virtualbox forums. You did a awesome job.

---

### Post by adrianhb on 2011-07-11
> **gizmo720 said:**
> Can't you just copy the entire filestructure over, then install grub on the new system?

This is what I originally tried but it didn't work as there were other hardware differences that had nothing to do with the kernel, this is why in the end I worked out that /dev had to be excluded from the original backup, there are things in /etc you need to bring over from the old system, the only thing I found that you needed from the new install was fstab

Thanks fr the positive comments, this job took me two days to work out, I was so close a number of times so I just had to keep at it until I won. I was able to learn so much from other peoples posts I just had to share too.

---

### Post by cha0s619 on 2011-07-11
thanks

---

### Post by bartgrefte on 2011-09-12
Would this howto also work with Debian?

---

### Post by adrianhb on 2011-09-26
It should work for most linux versions

---

