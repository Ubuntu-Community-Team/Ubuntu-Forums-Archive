---
title: "Will not finish booting /etc/fstab cannot yet be mounted"
date: 2010-01-22
forum: General Help
---

### Post by ruetheday on 2010-01-22
I have never in a year had a problem with this d-boot system.  Two days ago I tried to boot into ubuntu like every day.  It started to load normal, went to the ubuntu logo and paused for about 15 seconds and posted this under the logo:



One or more of the mounts listed in /etc/fstab cannot yet be mounted 
/: waiting for /dev/loop0
/tmp: waiting for  (null)
/boot: waiting for /host/ubuntu/disks/boot
Press ESC to enter a recovery shell
 



I have looked everywhere and tried so many things, I can't look any further.  All I have been doing for two days is trying to boot this system.  I really hate to say thank you to windows for being on the drive too or I wouldn't be able to research this bug.  

SOMEONE HELP.....PLEASE.... no really ….help

---

### Post by hwttdz on 2010-01-22
Can you post the output of

cat /etc/fstab|grep -v "^#"

and

sudo fdisk -l

and

ls -l /dev/disk/by-uuid

You're going to need to run both of these from the recovery prompt (which interestingly means you probably don't need to prepend sudo to the second command).  You can pipe the output to a drive that you can access from your windows partition by running "command > file_to_save_as.txt" just make sure you know where you're saving it, or you can just transcribe, but if you go that way be careful with the writing.

To give you an idea what these do, the first shows us what disks your machine is attempting to mount at system boot.  The second and third show what disks are mounted and a bit more information about the disks (hopefully).

Also while you're at the recovery prompt you might want to update & upgrade (sudo apt-get update && sudo apt-get upgrade).  It seems that this is complaining about some sort of a problem with your cd/dvd drive.

---

### Post by ac7ss on 2010-01-22
I have also had trouble mounting on boot. 

it gives me a 

```
 EXT3-fs warning (device sdb1): ext3_orphan_get: bad orphan inode 147633!  e2fsck was run?
``` in the messages log when I do mount it. System runs fine after that... You may want to start from a live disk and check the hard drive for errors.

---

### Post by hwttdz on 2010-01-22
> **ac7ss said:**
> I have also had trouble mounting on boot. 

it gives me a 

```
 EXT3-fs warning (device sdb1): ext3_orphan_get: bad orphan inode 147633!  e2fsck was run?
``` in the messages log when I do mount it. System runs fine after that... You may want to start from a live disk and check the hard drive for errors.

Start a new thread to avoid confusion, but it seems to think you ran e2fsck on a mounted disk, which is not a terribly good thing and it's recommending you run e2fsck from a livecd (to check the drive for errors and whatnot).  Or if it's not the / drive you can e2fsck it after unmounting.

---

### Post by ruetheday on 2010-01-22
> **hwttdz said:**
> Can you post the output of

cat /etc/fstab|grep -v "^#"

and

sudo fdisk -l

and

ls -l /dev/disk/by-uuid

You're going to need to run both of these from the recovery prompt (which interestingly means you probably don't need to prepend sudo to the second command).  You can pipe the output to a drive that you can access from your windows partition by running "command > file_to_save_as.txt" just make sure you know where you're saving it, or you can just transcribe, but if you go that way be careful with the writing.

To give you an idea what these do, the first shows us what disks your machine is attempting to mount at system boot.  The second and third show what disks are mounted and a bit more information about the disks (hopefully).

Also while you're at the recovery prompt you might want to update & upgrade (sudo apt-get update && sudo apt-get upgrade).  It seems that this is complaining about some sort of a problem with your cd/dvd drive.

the output is normal, the boot drive says fat however i know it is not, common output error.  I have a suspicion it is my SD drive.  It almost boots then nothing.

---

### Post by ruetheday on 2010-01-25
when i df /boot i get 

/dev/sda1    *    1   38913    312568641    c    w95 fat32 (lba)


....nw the maintenance shell just crashed    why is boot a *?  i went into g parted using the latest live cd and it said to check with windows checkdisk and i did and now that seems to be fixed...  why can't i get this thing going..\


anyone have any idea how i  can get a better output of what is going on?   this to me is a major bug....

---

### Post by ruetheday on 2010-01-25
so now when i recover boot it almost loads then near the end fills the page with 14 or so lines that are exactly the same:


udevd[2479]: inotify_add_watch(6, (null), 10) failed: bad address
udevd[2479]: inotify_add_watch(6, (null), 10) failed: bad address
udevd[2479]: inotify_add_watch(6, (null), 10) failed: bad address
udevd[2479]: inotify_add_watch(6, (null), 10) failed: bad address
udevd[2479]: inotify_add_watch(6, (null), 10) failed: bad address

then it stops the firewall and posts my original text...one or more.....

---

### Post by ruetheday on 2010-01-25
i just tried mountall and got this

swapon: /host/ubuntu/disks/swap.disk: swapon failed: device or resource busy
mountall:swapon /host/ubuntu/disks/swap.disk [3057] terminated with status 255
mountall problem activating swap: /host/ubuntu/disks/swap.disk


then my original post of one or more mounts listed...
how do i know what is causing this?  i am aboot to freak out

---

### Post by ruetheday on 2010-02-09
Seriously, anyone have an idea?  Can i edit my grub load?  or is there something  in windows that might be missing or corrupt? (registry?)

---

