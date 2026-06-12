---
title: "GDM could not write to your authorization file"
date: 2006-04-20
forum: General Help
---

### Post by evaristegalois on 2006-04-20
I got my harddrive too full and have run into the following problem: I can no longer log in because I will get an error message saying:

"GDM could not write to your authorization file . . ."

It would, of course, be nice to be able to go in and delete a few files but, alas, no luck. I am also not the first person to have run into this, and what people advise is to run ubuntu off the live CD, mount the partition on which home is located and then delete a few files. I ran the live CD and entered in the terminal window:

ubuntu@ubuntu$ sudo mount -t vfat -o uid=ubuntu,gid=users /dev/sda1 /home/myname

after creating the /home/myname directory. The funny thing is the command went through but I don't see a thing under /home/myname even though according to fdisk /dev/sda1 should be the harddrive partition where all my files sit.

Any suggestions? Any other ways of getting out of the "GDM could not write to your authorization file . . ." quandary where your harddrive is full and the computer won't let you log in to remove files?

--evaristegalois

---

### Post by verbalshadow on 2006-04-20
Have you tried the Rescue boot in grub menu?

---

### Post by tay on 2006-04-20
i had that problem before also

you are using a sata drive.. i had ext2fs

hm.. about 5 months ago..

anyways..

$sudo mount -t ext2fs /dev/hda1 /mnt
$cd /mnt
$ls
$cd /mnt/home/Desktop/Shared/
$sudo rm ./Shared

something like that..

$umount

don't remember if rm worked on a directory,, much faster than individual files.

---

### Post by evaristegalois on 2006-04-21
Thanks both of you. Solution #1 worked just fine. Don't use live CD. Reboot. When grub comes up press <ESC>. Start up in ``recovery mode.'' Remove files by command line

rm filename

or whole directories recursively (know what you are doing!) by

rm -r directoryname

Restart.

--evaristegalois

---

