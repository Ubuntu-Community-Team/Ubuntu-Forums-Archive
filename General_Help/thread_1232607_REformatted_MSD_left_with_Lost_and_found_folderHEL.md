---
title: "REformatted MSD left with Lost and found folder???HELP pls"
date: 2009-08-05
forum: General Help
---

### Post by slick1a on 2009-08-05
i have a dilema.

I noticed that the 8gig card in my fone was missing 5.6gig allowing me not to have the full capacity in use...

at this point i tried : reformatting in my fone - no joy there, then i tried the following:

slick@slick-desktop:~$ sudo mkfs.ext3 /dev/sdf1
mke2fs 1.40.8 (13-Mar-200
/dev/sdf1 is mounted; will not make a filesystem here!
slick@slick-desktop:~$ sudo mkfs.ext3 /dev/sdf1
mke2fs 1.40.8 (13-Mar-200
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
485760 inodes, 1939456 blocks
96972 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1988100096
60 block groups
32768 blocks per group, 32768 fragments per group
8096 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
slick@slick-desktop:~$ sudo e2label /dev/sdf1 usb-pen-fone

SDF1 - is the usb Sd card in question from my fone, however when i reinsert said card to my fone , the fone will not recognise it as external memory!

I fear i have turn my sd card into something else!

Whilst the above in part worked, illiminating all previous folders and returning my missing capacity, im left with only one folder "lost and found" unable to create another folder along side it but able to create a folder within and to write to the lost and found folder.

but alas my fone will not read or find this folder..my fone is not the problem here...its my poor teching.

---

### Post by slick1a on 2009-08-05
ive also enabled gparted:

slick@slick-desktop:~$ sudo gparted
=====================
libparted : 1.7.1

i need to be able to read a file from my fone again and to create folders??

if gparted is for partitioning only it will not serve my purpose.

---

### Post by slick1a on 2009-08-05
The unallocated is just an image and video file i added into the lost and found folder..

why is the rest locked and more importantly how do i unlock it?

---

### Post by slick1a on 2009-08-06
k, ive worked out how to resize using gparted...

i tried the msd card in my dvd player last night , again this was not a recognisable format when it once was.

---

### Post by Cheesemill on 2009-08-06
I'm pretty sure that most phones only recognise a FAT32 filesystem.

---

### Post by bryncoles on 2009-08-06
Now I'm no expert, but looking at your first post, it looks like you might have reformatted the sd card into ext3 format. 

please plut it back into your computer and run ```
sudo fdisk -l
``` so we can look. 

or / just **CAREFULLY** reformat the sd card in fat32 format (i say carefully because you dont wanna do the wrong drive!)

---

### Post by slick1a on 2009-08-06
Thanks guys...

Yhea it was my formatting skills or lack there of..

The fone now recognise's the msd card having now reformatted using gparted to fat 32.

MSD card now works in fone and dvd player !!!

Big smiles here!!!

---

