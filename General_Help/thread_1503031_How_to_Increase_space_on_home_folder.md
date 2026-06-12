---
title: "How to Increase space on home folder ?"
date: 2010-06-06
forum: General Help
---

### Post by Joao Lacerda on 2010-06-06
Hello Friends!
 I do need some help.
 I have installed ubuntu on my second hd, the size of is 500 GB.
 The live Ubuntu cd installation have used only 250 GB, the rest remains as NTFS system.   
 And now I do need more space on my home folder, I would like to  convert the 250 GB NTFS to Linux system and add it to my home folder. But I don't know how. I have looked at Disk Utilities, I have not found this possibility. Can some help on this?  
 

 Thanks in  advance.

---

### Post by bigmojo74 on 2010-06-06
Joao,
I've heard of things like Partition Magic that allow you to resize existing permissions, but personally I've never used such a utility - and have to say I think the concept is abit sketchy.

As a suggestion for an alternative to actually redefining your partition table, you could always simply format the 250GB partition then simply mount it. Keep in mind you're not limited to mounting everything under / either, you could for example mount it as /home/bigmojo/music - that way it appears like it's a folder under your home directory, but is secretly another partition all together. I like to think of it as a pocket dimension myself...

Anyhow I'm relatively new to the Gnome GUI and Ubuntu so I'm not sure how you'd do this graphically, it's probably pretty simple, but via CLI it'd look something like:
sudo mount /dev/sda9 /home/bigmojo/Music

---

### Post by warfacegod on 2010-06-06
You'll need to put your installer CD in and boot from that. Select "Try Ubuntu without making changes"

Once it loads, go to:

System> Admin.> Gparted

Right click the HDD and make sure it isn't mounted (it's probably sdb)

Now delete the partition that you don't want. Click Apply.

Right click the partition that you want to make bigger and select resize. Drag the arrows to the desired size. Click Apply.

***_[SIZE="3"]MAKE A BACKUP FIRST![/SIZE]_***

---

### Post by colorlessprism on 2010-06-06
i agree with bigmojo, you would probably be better served formating the partition and mounting it. 

this is what i would do (cause it what i did do). i made 5 partitions; documents, pictures, videos, music, wine. they are mounted under /mnt/<name>. then i created symlinks on my home folder for each partition. now when i click "documents" the computer thinks im at /home/<login>/Documents when its really at /mnt/documents. the benifit is when i reinstall, i do this for release testing, i do not have to move all this information back 
you do not want to mount the partitions directly in your /home because then you will have a shortcut on your desktop for each partition you create and another shortcut in nautilus. by having the mounted in another place (like /mnt) you can avoid having a dekstop filled with shortcuts. 
you will need to edit your fstab to have everything mounted for you. i have included a copy of mine for reference:
__________________________________
 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /mnt/wine was on /dev/sda9 during installation
UUID=18cc9169-76af-45ff-aed7-63a4f5c1615b /mnt/wine ext4    nodev,nosuid        0       2
# /mnt/documents was on /dev/sda5 during installation
UUID=3103ae55-ef58-4690-9573-1121318bfdf9 /mnt/Documents ext4    nodev,nosuid        0       2
# /mnt/music was on /dev/sda6 during installation
UUID=16544e79-abc8-49e6-a4ba-323e7ad122c7 /mnt/Music ext4    nodev,nosuid        0       2
# /mnt/pictures was on /dev/sda7 during installation
UUID=7eaa70ad-91ca-4737-82a6-db7e8739af4b /mnt/Pictures ext4    nodev,nosuid        0       2
# /mnt/videos was on /dev/sda8 during installation
UUID=e84643ea-33c1-4d84-8f98-4f7f4e32bcbf /mnt/Videos ext4    nodev,nosuid        0       2
# swap was on /dev/sda10 during installation
UUID=651b5620-1632-4571-bc78-b8b18bed88bb none            swap    sw              0       0
_______________________________________________

---

### Post by Joao Lacerda on 2010-06-06
Thanks for helping.

It was not possible to merge the new partition to home folder. What I do have now is a new volume, mounted at /media/new volume. 
But it is OK, I will move my date to this volume and I think that it is solved for now . and the next time that will reinstall the new ubuntu, it will be easy to make just one volume. 

Thanks again..

---

### Post by linuxman94 on 2010-06-06
Here is a tutorial for using a separate home partition.

[Separate Home]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by leehach on 2010-06-08
Check out what warfacegod said. I have done this to resize partitions. You can definitely use gparted to delete the NTFS partition, and then increase the existing /home partition to take over the space that is now unallocated--as long as the /home partition is physically next to the unallocated space.

It's also possible to resize and move unmounted partitions while running Ubuntu from your hard disk, so you would be able to delete the NTFS partition, but of course you can't resize the /home partition while you're using it. That's why you need to boot up from the Live CD.

---

