---
title: "Partition Ubuntu for maximum speed?"
date: 2009-07-10
forum: General Help
---

### Post by ArtF10 on 2009-07-10
I keep reading how it is recommended that Windows users create 2 separate partition on a single HDD - one for the operating system and the other for everything else inorder to obtain maximum speed/performance out of the drive.  I have no idea what this is supposed to do because, to me atleast, at the end of the day its STILL THE SAME DRIVE!!!  Anyways, presumably, there's some benefit to doing this.

Well, I don't use Windows so here's my question:

Assuming that the user will perform a fresh install of Ubuntu(wipe out ENTIRE hard drive) as soon as a new version is released, what's the best way to set up the partitions, on a single 7200 RPM IDE/SATA/SATA-II internal hard disk drive, so as to extract the maximum speed out of a fresh Ubuntu installation(ext4)?

---

### Post by ArtF10 on 2009-07-10
Guys your help would be greatly appreciated.  I am ready to do a fresh install for some relatives who recently transitioned to Ubuntu(Linux in general) and I'd like to sort this out now than keep bugging them frequently.  Your help would really be of great assistance as I haven;t done this before.

---

### Post by starcraft.man on 2009-07-10
Uh, I think you misread. I think what your talking about is having two partitions one for root (/) which holds all the main directories. A second partition, with most of the rest of your HDD, would be dedicated to /home partition, where all the user files go. This is where you would keep videos, music, pictures, anything else. It gets large very quickly compared to /.

I don't think it's primarily a speed advantage thing, having two partitions on the same drive in this configuration is designed to give protection for user files. If something happens to the root partition, you can format over it and mount home again to the /home mount and have all your program configuration files as well as your personal files. I do this on all my machines, I think it's important and just good practice, I don't do it for speed though.

Basically, root needs no more than 10 or 12 GB tops (a generous estimate), the rest you can dedicate to /home. I don't see any value in having additional partitions from root mounted separate like /boot or /var...

If you need and help or documentation, see [gparted]("http://gparted.sourceforge.net/documentation.php").

To get any real speed advantage, you need to set up something like a raid 1 array for striping, or put home and / on separate drives. I don't think it's required for the average user.

---

### Post by jbusch on 2009-07-10
You might want to read this article about the use of partitions.  It's for XP users, but the basic concepts apply pretty well to any system in which you might perform partitioning.  
[http://www.theeldergeek.com/hard_drives_02.htm](http://www.theeldergeek.com/hard_drives_02.htm)

The only partition that MIGHT make a speed difference is swap space.  Swap acts as extra RAM, though not quite as fast or efficient.  A good rule of thumb would be to have the amount of swap space equal to the amount of physical RAM you have.  Unless RAM is at a premium, in case you might want a little more.

- J

---

### Post by amauk on 2009-07-10
How you partition your drive has absolutely no bearing on performance
(local partitioning - ignoring NFS)

Partitioning allows more flexibility in how you use and manage your system, that's all

There are certain root directories that benefit, management wise, from being mounted from a dedicated partition / drive

These can either be local partitions, or partitions on another machine (NFS network shares)

**/home**
all user home directories on dedicated partition means you can wipe the system & reinstall without affecting user files
just remount /home on a newly installed system, and all your personal files & system preferences are kept intact

**/usr**
moving /usr to a dedicated partition is beneficial if you have a large install (many programs installed)
The more stuff you install, the bigger /usr gets
If it's on a dedicated partition, it's simple to migrate your user programs to a larger hard disk should you need more space

**/boot**
I think this tip is obsolete now-a-days
but a few years back, many motherboards would only boot off of the first 1024 cylinders
having /boot on a dedicated partition eased the problem with large disks on legacy motherboards
but again, I think this is now obsolete, as BIOS's have had large disk support built-in for some time

You can also move /var & /tmp to separate partitions, should you choose

---

### Post by raymondh on 2009-07-10
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)


And just in case the installer cannot see your SATA drive, try the alternate install method.

Back up files first.  Good luck.

---

### Post by ArtF10 on 2009-07-10
alright, well, I guess that solves that.  I must have misread.

---

