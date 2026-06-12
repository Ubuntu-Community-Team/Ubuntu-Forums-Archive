---
title: "need help moving files from 1 partition to another in terminal"
date: 2011-12-15
forum: General Help
---

### Post by shanep-server on 2011-12-15
I need to move a folder an all folder behind it to another partition on the same hard drive.. I'm using ubuntu server.. I have a 2tb hard drive.. i shrank the size of the partition and created 2 more partitions.. 1 partition has system files.. the 2nd will be used after I reformat to hold /home and the 3rd partition is where I need to transfer files too (from the first partiton holding ubuntu server) Note that the server i'm using has only 1 hard drive.. a 2tb sata drive.

I don't know the commands to list the partitions 

i tried "fdisk -l /dev/sda/" but it returned "cannot open /dev/sda/

I also don't know how i'm going to mount the 3rd partition so I can transfer files too it via the terminal

I tried to use a live cd to move the files with a gui but it said i didn't have permission..

Any help would be appreciated

---

### Post by Synoc on 2011-12-15
to add the third partition as an permanent mount on your server, you have to edit the /etc/fstab file (WARNING back up the file BEFORE EDITING) 
```
 cp /etc/fstab /etc/fstab.old 
```

afterwards you simply add a line to the fstab file
assuming a standard HHD with an sdX naming convention and that it is the first hard drive and THE third partition on that drive... you just need to decide where you want to mount it. for example mounting it on a folder (named file-storage) off of root 
```
 sudo mkdir /file-storage 
```
then add this line (or one similar) to you fstab
```
/dev/sda3 /file-storage ext4 -w 0 0 
```
tab between fields to make it more easily readable for you. the exact those are the values for the fields that are explained in the fstab file. with the < > around them. this option will mount as readable/writable (this is default but good practice IMO)

if you want to mount it temporarily, just to move the folder, type
```
 sudo mount /dev/sd3 /mnt 
```
that will will mount the partition to the the /mnt folder where most manually mounted file systems go for good practice. it will unmount when you power down the system or a 
```
 sudo umount /dev/sd3 
```
is entered. 

to MOVE the folder from one partition to another is straight forward
```
mv /path/to/folder/ /destination/path/ 
```

---

### Post by shanep-server on 2011-12-15
after editing the fstab file followed by a reboot.. i got an error.. failed too mount /storage <-- the name i used for /file-storage

i could hit S to skip mount or M for manual

after hitting S it booted my server and at the top above my server info.. 

11.861740} EXT4-fs (sda4): Unrecognized mount option "-w" or missing value

i tried sda3 and sda4 to no avail

---

### Post by shanep-server on 2011-12-15
I think i'm getting it done under temp mount.. thanks for the help

---

### Post by fdrake on 2011-12-15
i hope you did a backup of fstab...
enter recovery mode: when booting the sys keep the "shift" key pressed untill you see the grub menu> press shift > in recovery mode select run shell prompt as root and type
```

less /etc/fstab.old > /etc/fstab
reboot

```
if now you can boot normally we can try to fix your original issue... post the results of the following commands:
```

sudo fdisk -l
sudo parted -l

```

---

### Post by shanep-server on 2011-12-16
I managed to achieve my current goal with the temporary mount.. Right now I'm content with where I'm at and moving forward with redoing my server with a better setup.. 

Thank you all for your time and help.. I really appreciate it

like usual ubuntu forums to the rescue :)

---

### Post by Synoc on 2011-12-16
someone please correct me if I am wrong on this...

I errored in my syntax, it's not "-w". it is "rw"

also if you could post the output of ```
 df 
``` it would help 

do so while you have your partition temp mounted

I know you have it fixed well enough for now, but fixed perfectly is what we strive for here :)

do a copy/paste from terminal and place it in the "code" brackets (the # button above the text window."

If you are totally happy with the results, however, then please mark the thread as "Solved" or people like like me will keep trying to help :)

---

### Post by scorchgeek on 2011-12-16
For the record, your original problem was caused by not running fdisk with sudo.

---

