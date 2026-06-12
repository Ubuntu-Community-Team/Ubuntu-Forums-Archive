---
title: "Browsable partition images for EXT4/FAT32/NTFS partitions?"
date: 2010-10-01
forum: General Help
---

### Post by pastapasta on 2010-10-01
I would like to create partition images for a dual boot Ubuntu 10.04 64 / Windows 7 64 system. There are ext4, FAT32 and NTFS partitions that I would like to create images of. I would also like to be able to browse and extract files from the images I create.

[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging) hasn't been helpful at all.
The recommended Partition Image software doesn't support ext4. And Clonezilla  doesn't support exploring (or mounting) of images you create.

I'm looking for something that I could teach someone less computer literate to use, so CLI solutions like dd are not what I'm looking for. 

If there really aren't any FOSS GUI based solutions right now, what are the closed source software solutions that I could look into?

---

### Post by pastapasta on 2010-10-01
So there is no easy (partition based) backup solution for Linux systems running on ext4 partitions?


So what am I supposed to do to being able to recover from HDD failures or malware infections?


I wish there would have been a warning while installing Ubuntu 10.04 64 that ext4 isn't yet supported by the recommended partition imaging software. :(

---

### Post by srs5694 on 2010-10-02
> **pastapasta said:**
> So there is no easy (partition based) backup solution for Linux systems running on ext4 partitions?

Programs like tar and cpio are filesystem-independent and will do the job. They aren't GUI, but there are GUI front-ends to them, although it's been quite a while since I've looked into such tools. (I prefer just using them from the command line.)

---

