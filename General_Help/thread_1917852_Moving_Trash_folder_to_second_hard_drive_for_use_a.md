---
title: "Moving Trash folder to second hard drive for use as archive?"
date: 2012-01-30
forum: General Help
---

### Post by shamusl on 2012-01-30
I would like to move the trash folder to my second hard drive that isn't on my SSD, so it can reside on my 3TB storage drive. I would like to use the Trash as a kind of archive, because I really have no reason to ever delete anything anyway. Can anyone help me with this? Also, does it complicate things for distro upgrades, etc.?

---

### Post by Bobhuber on 2012-01-30
> **shamusl said:**
> I would like to move the trash folder to my second hard drive that isn't on my SSD, so it can reside on my 3TB storage drive. I would like to use the Trash as a kind of archive, because I really have no reason to ever delete anything anyway. Can anyone help me with this? Also, does it complicate things for distro upgrades, etc.?
Actually thats a good idea. I delete everything but if you move things to the trash bin that would be the place to put them with an SSD drive.  Your trash directory is in your home directory (hidden directory)  .local/share/Trash
The easiest way to do this would be to right click on the directory in Nautilus and copy the directory to your second drive .This will move the directory (Trash) and the (2) sub directories to the new location. Then delete the original directory and make a sym link to the new location. From a terminal in your home directory .

ln -s /media/ <name of your second location>/Trash /home/bob/.local/share/Trash

Replace bob with your login name of coarse.

---

### Post by shamusl on 2012-01-30
> **Bobhuber said:**
> Then delete the original directory and make a sym link to the new location. From a terminal in your home directory .

ln -s /media/ <name of your second location>/Trash /home/bob/.local/share/Trash

Replace bob with your login name of coarse.

I've copied the trash folder where I want: /sdb5/Trash, but that command above is just outputting "Is a directory" 

Is this not how symlinks work?

---

### Post by shamusl on 2012-01-30
Okay. I've created the Symlink which is for some reason in /media/sdb5/Trash/Trash. Files appear in the new symlink but if I delete /home/shamus/.local/share/Trash, nothing deletes to trash (invalid argument) and the symlink breaks.

---

### Post by Bobhuber on 2012-01-30
> **shamusl said:**
> Okay. I've created the Symlink which is for some reason in /media/sdb5/Trash/Trash, files don't seem to be copying into that folder, so I'm a bit nervous to delete the default trash location with root.
Delete the sym link you made. It is not correct.
Where do you mount the second drive ? Are you mounting it when you boot the machine ?
The sym link should point to the mount point on the second drive. sdb5 is a partition name and NOT the mount point of the drive. 
For instance I mount my second drive during boot with the following command in fstab file. Please note this is for MY machiine and will not work for you . The UUID will be different.

/dev/disk/by-uuid/e4b05e79-bc82-4046-b9bd-fa3fc66fe74b /media/secondary    ext4

I made a directory /media/secondary . secondary is the mount point for my drive.
Once the drive is mounted all reference and links to it are now /media/secondary
If this is a bit over your head I hesitate to go any further untill you do a little research on drive partitioning,mount points and using UUID for drive identification . You will have to make modifications to your fstab boot file and update grub before you start making sym links to the second drive which is highly recommended for storage with an SSD drive as your boot.

---

### Post by shamusl on 2012-01-30
> **Bobhuber said:**
> Delete the sym link you made. It is not correct.
Where do you mount the second drive ? Are you mounting it when you boot the machine ?
The sym link should point to the mount point on the second drive. sdb5 is a partition name and NOT the mount point of the drive. 
For instance I mount my second drive during boot with the following command in fstab file. Please note this is for MY machiine and will not work for you . The UUID will be different.

/dev/disk/by-uuid/e4b05e79-bc82-4046-b9bd-fa3fc66fe74b /media/secondary    ext4

I made a directory /media/secondary . secondary is the mount point for my drive.
Once the drive is mounted all reference and links to it are now /media/secondary
If this is a bit over your head I hesitate to go any further untill you do a little research on drive partitioning,mount points and using UUID for drive identification . You will have to make modifications to your fstab boot file and update grub before you start making sym links to the second drive which is highly recommended for storage with an SSD drive as your boot.

Well, in the process of trying different things with my drives, I restarted and my motherboard refused to boot, halting at "Verifying DMI pool data......." It also won't boot from CD, when I pull the battery and reset the CMOS on the board, it simply spits out: "No operating system" infinitely in a loop. Good news is that for some reason USB was found, and I was able to boot that way after a lot of tinkering.

You live and you learn I guess.

---

### Post by Patb on 2012-10-23
So is there an answer to this? Can the trash folder be moved to a different drive? I tried creating a symlink but I get an error "invalid cross device link" when I try to delete any file. 

Cheers, Pat.

---

### Post by jb0nez on 2013-04-15
I'm using kubuntu with a small /home on my SSD; all the other major directores are bind mounted in my fstab to a kubuntu 12.10 120GB install on my HDD. To decrease wear on my SSD I'd also like a solution to this.

---

