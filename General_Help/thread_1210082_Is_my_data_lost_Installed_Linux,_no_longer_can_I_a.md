---
title: "Is my data lost? Installed Linux, no longer can I access my hard drives."
date: 2009-07-11
forum: General Help
---

### Post by Newatthislol on 2009-07-11
Here's the story -

I installed Linux on my Y drive, and all went well until I tried to boot into XP again. I can't access or install an operating system to my other three hard drives, C, X, and Z.

I think that during the install my hard drives were changed to something other then NTFS, but Linux won't access them either.

When I use my Windows XP or Windows 7 disc, it says the drive has 0mb free, and it can't install until I delete the partition, then reformat. I don't want to do this obviously, because I don't want to format all of my data.

When I go to Places > My Computer it lists my CD drive, Filesystem, and the Y drive. It doesn't show my other three hard drives.

Under Palimpsest Disk Utility I can see my other three drives, but I can't access the data on them yet.

Help!

---

### Post by lindsay7 on 2009-07-11
type sudo fdisk -l   (the letter l, small case) into the terminal.  This will show your drives and how they are configured, and post the results here.

---

### Post by Newatthislol on 2009-07-11
I don't think this is what you wanted, but this is what I got - 

[PHP][liveuser@localhost ~]$ sudo fdisk -l 

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

liveuser is not in the sudoers file.  This incident will be reported.
[liveuser@localhost ~]$ sudo fdisk -l[/PHP]

---

### Post by lindsay7 on 2009-07-11
Are you sure you typed in the letter L small case in the command

sudo fdisk -l


Did you use the terminal found under Applications/accesories/terminal

---

### Post by Newatthislol on 2009-07-11
Yes, I am sure. First I typed it myself, and when that didn't work I copy/pasted into terminal, which I found by going to Applications > System Tools > Terminal.

[PHP][liveuser@localhost ~]$ sudo fdisk -l
liveuser is not in the sudoers file.  This incident will be reported.
[liveuser@localhost ~]$ 
[/PHP]

---

### Post by Newatthislol on 2009-07-11
Alright - it looks like I've got what you want - 

[PHP]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00ca89b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3de4bf44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   17  Hidden HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76397639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32dbca08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   8e  Linux LVM

Disk /dev/sde: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf03b4104

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       10338    78147584    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
[/PHP]

---

### Post by QIII on 2009-07-11
Was your XP install on the 80GB drive?

In the terminal, type

```
sudo gedit /boot/grub/menu.lst
```

DON'T change anything.

Cut and paste the results back here.

---

### Post by lindsay7 on 2009-07-11
Ok, thanks, but I am lost here. Do you have a raid installation going on here or something different?  First of all, I so not see any partitions maked as boot partitions. There is a hidden file system on one drive (Hidden HPFS/NTFS) and one marked as (HPFS/NTFS) and two drives are marked as Linux LVM.

I have never seen these before and I have no idea about what is going on, so I am going to stand back and watch you thread for answers. Sorry I can not help and good luck to you.

---

### Post by QIII on 2009-07-11
Looks like he set up a RAID.  Otherwise, I'm not sure why he went with logical volume management.

---

### Post by Newatthislol on 2009-07-11
> **QIII said:**
> Looks like he set up a RAID.  Otherwise, I'm not sure why he went with logical volume management.

No, I didn't set up a raid. Everything was running smoothly until I had to cancel the Ubuntu set up...

When I type sudo gedit /boot/grub/menu.lst into terminal, gedit appears with menu.lst open.

The file is blank, here's a screenshot -

[http://img16.imageshack.us/img16/4283/26994679.gif](http://img16.imageshack.us/img16/4283/26994679.gif)

---

### Post by QIII on 2009-07-11
Beats the fertilizer outta me, then...

---

### Post by lindsay7 on 2009-07-11
You may be able to use Gparted to unhide the partiton shown

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   17  Hidden HPFS/NTFS

```

Open Gparted it is under systerm/administration/partition editor and right click on the drive and partition.  If it shows hidden and it checked you can uncheck it and see if you can access your data on that drive.

Do you remember seeing anything during the install that talked about the Lilo boot loader?

---

### Post by Newatthislol on 2009-07-11
> **lindsay7 said:**
> You may be able to use Gparted to unhide the partiton shown

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   17  Hidden HPFS/NTFS

```

Open Gparted it is under systerm/administration/partition editor and right click on the drive and partition.  If it shows hidden and it checked you can uncheck it and see if you can access your data on that drive.

Do you remember seeing anything during the install that talked about the Lilo boot loader?

No, I don't remember seeing anything about Lilo. 

I managed the flags so that none of the hard drives have a 'hidden' flag anymore, but it still doesn't allow me to go to Places > My Computer and look at what's on the drives.

It says 'filesystem unknown, which is (my assumption/guess) why I can't look at what's on the drives. Unfortunately, the only option to switch it to NTFS includes formating, which I am absolutely **not** excited about.

---

### Post by lindsay7 on 2009-07-11
This may help you

[http://ubuntuforums.org/showthread.php?t=396629](http://ubuntuforums.org/showthread.php?t=396629)

I you are using the live cd Ubuntu viewing these may just be temporary, since you can not save a setting to it.  I would think you could see the drive from windows. Or you could install Ubuntu or one of the distros like Slitaz to a usb drive and use it to move you ntfs files around until you figure out how to get your system back.

---

