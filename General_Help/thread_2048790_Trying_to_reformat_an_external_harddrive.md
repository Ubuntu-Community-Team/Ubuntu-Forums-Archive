---
title: "Trying to reformat an external harddrive"
date: 2012-08-27
forum: General Help
---

### Post by fbjoey on 2012-08-27
Hi

I'm trying to install an external hard drive to use as a storage device for transferring files from my Mac to Ubuntu. The hard drive at the moment is formatted to be used as a Time Machine for my Mac. 

I've been following this thread to reformate it to Fat32 [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive). I'm using gparted and in step one it says right click on the white bar and select new. However the new selection is not highlighted.

because this didn't work i tried to do with the command line. 
I typed "sudo fdisk /dev/sdb" like it says in step one. "WARNING: GPT (GUID Partition Table)" detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted."


Does anyone no what the problem is?
Cheers for any help
Joey

---

### Post by spiky001 on 2012-08-27
Hi   Can the mac not format the drive, might work out easier.

---

