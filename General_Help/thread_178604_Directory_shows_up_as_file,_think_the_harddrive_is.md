---
title: "Directory shows up as file, think the harddrive is dieing."
date: 2006-05-18
forum: General Help
---

### Post by Abdi110 on 2006-05-18
Hi. So first off, 1) I'm still a newb at Linux, 2) don't buy refurbished drives. I got 2 250 gig WD drives off of woot.com for $50 each. Sounded like a good deal three months back, it wasn't.

My server has been having problems playing back video content on other systems around the home for the past week. I just had some time tonight to see what was the matter, did a quick reboot only to find the bios beeping a bunch of times and not running the boot loader. After an hour of trying to find an extra monitor, keyboard and mouse I find the bios telling me that one of the drives has a S.M.A.R.T. bad drive error, gives me the option to press F1 to continue. I do.

The partition seems like it's mounting, but when I go to that dir to see about copying the data off to another drive, the sole directory under the root dir for the partition is showing up as a file.

abdi110@crypt:/crypt/node/c$ ls
lost+found  videos
abdi110@crypt:/crypt/node/c$ cd videos
bash: cd: videos: Input/output error

mtab shows it's mounted. Don't know what to do. Any help would rock, thanks.

EDIT:

abdi110@crypt:/crypt/node/c$ sudo umount /dev/hdd1
umount: /crypt/node/c: device is busy
umount: /crypt/node/c: device is busy
abdi110@crypt:/crypt/node/c$

Sad.

Ok, I'm dumb, don't leave other windows open. :(

2nd EDIT:

Is there some sort of disk doctor for Linux, sort of like Norton for Windows?

---

### Post by nanotube on 2006-05-18
well, if there is a smart error, then your drive is def going bad, and you need to replace it, no question about it. since its only been three months, should still be under warranty.

as for "disk doctor", there is command "fsck" (or e2fsck, if your disks are formatted with ext3). man both of these for more details.

i am not aware of a gui-based diskcheck tool, but i'm sure there are a few.

---

