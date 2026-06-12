---
title: "Merge Harddrive space without reinstalling ubuntu"
date: 2010-03-10
forum: General Help
---

### Post by madscientist032 on 2010-03-10
Hi all.

I currently have Ubuntu 9.04 installed on my HP Pavilion A1213W alongside Windows XP. Problem is, I no longer need the XP partition (finally) but I would like to reclaim the rest of the hard drive for Ubuntu. 

I'm planning on wiping the XP partition with GParted and then (hopefully) I can merge the unallocated space with my existing 9.04 partition without having to reinstall Ubuntu and lose all my stuff. 

Is there a way to do this? I have nothing to back my hard drive up to other than a 2 gig flash drive. 

Thanks in advance.

---

### Post by mechro on 2010-03-10
If you make "unallocated space" then Gparted can enlarge a partition to use this space.

Note that you should back-up if you're doing any partition manipulation of a working system. If you don't it's at your own risk.

---

### Post by madscientist032 on 2010-03-10
> If you make "unallocated space" then Gparted can enlarge a partition to use this space.

Does this mean that after formatting the XP partition as "unallocated space", I use the "resize/move" function to enlarge the 9.04 partition so that it takes up the rest of the hard drive?

(and it's not the windows data I'm worried about - it's the Linux stuff I need to keep)

---

### Post by mechro on 2010-03-10
> **madscientist032 said:**
> Does this mean that after formatting the XP partition as "unallocated space", I use the "resize/move" function to enlarge the 9.04 partition so that it takes up the rest of the hard drive?



Yes, as long as the space and the partition you want to resize are adjacent. If they're not adjacent you may have to move a partition first but eventually you'll end up with your enlarged partition. Gparted should do all this without affecting the data on your partitions but the warning about backing up is just in case!

---

### Post by madscientist032 on 2010-03-10
In the rare case I find a harddrive bigger than 20 gigs around here, what's the best backup method / utility for linux? (other than drag-n-drop or copy & paste)

---

### Post by mechro on 2010-03-10
Personally, I just right-click > Create Archive and then drag n drop or copy and paste the Archive but there may be better methods.

If nobody suggests anything else try searching the forums for other recommendations.

---

### Post by georgeen on 2010-03-10
I'm newbie but I had the experience to do something like you describe, and is quite easy and safe with GParted. For the backup the real important thing are the files you generate that usually are in home, so tar -zcvf /home <file with your stuff compress> and thats all maybe that compress file in your thumb drive and go on with GParted from a Ubuntu Live CD.

I hope that this help you, bye.

---

### Post by srs5694 on 2010-03-10
I recommend a completely different approach:


[list=1]
[*]Use fdisk, GNU Parted, GParted, or whatever to change the type of the Windows partition to 0x83 (Linux data). (If Windows occupied two or more partitions, you could instead delete them both/all and create one new bigger partition in its place.)
[*]Use mkfs, GNU Parted, GParted, or whatever to create an appropriate Linux-native filesystem on the former Windows partition.
[*]Mount the Windows partition somewhere convenient -- say, at /mnt.
[*]Determine the size of the Windows partition ("df -h /mnt" will do this).
[*]Determine the space used in various Linux directories, such as /usr, /home, and /var ("du -sh /*" will do this -- but you'll need to be root to get an accurate measure, and it'll take a while).
[*]Copy the data from a directory tree with a reasonable amount of space to occupy the newly-cleared Windows partition onto that partition. For instance, if /usr consumes 10G and the former Windows partition is 20G, and you're comfortable with that ratio, do "cd /usr; tar cpf - . | (cd /mnt; tar xvf -)". (Other copying methods, such as "cp -a", may also work.) Note that you *must not* move /etc, /bin, /sbin, /dev, /root, or /proc in this way.
[*]Boot into an emergency system. Verify that the former Windows partition has the files it should, then rename the original Linux directory (/usr in this example) to something else (/usr-old, say). (For some directories, such as /home, you can forego booting an emergency system, although you may need to log out of ordinary user accounts or shut down some programs.)
[*]Create a new empty directory for the directory whose contents you've just copied, using the original name (/usr in this example).
[*]While in the emergency system, edit /etc/fstab to add the new partition to mount at the appropriate location.
[*]Boot back into the regular installation.
[*]Once you're satisfied everything is working, delete the renamed old original directory.
[/list]


This may sound complicated, but it's likely to be safer, and perhaps faster, than moving/resizing entire directories. It also enables you to take advantage of multiple partitions to help keep your data safe. If you move /home, for instance, you'll be able to completely wipe and re-install Ubuntu without damaging your personal data. OTOH, if the preceding description completely baffles you, you'll probably find it easier to use GParted to move/resize your partition, as others have suggested. (You'll need to do so from an emergency system.)

---

