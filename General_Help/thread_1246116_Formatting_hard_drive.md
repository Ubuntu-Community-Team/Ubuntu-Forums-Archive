---
title: "Formatting hard drive"
date: 2009-08-21
forum: General Help
---

### Post by mercules2178 on 2009-08-21
I have been using ubu for a couple of months now and I finally wiped windows from my drive. I have two 250 gig drives, the first I partitioned and installed root into one partition and home into the other. The second I formatted ext4 and had to do searching as to why I could not access the drive. I found out that if you use gparted to format the drive it will use root and the user does not have access. Not cool, is there a way to change who has permissions to the drive? I am still going to need to allow windows to access part of the drive, so I am guessing that I will need to partition the drive and format one partition as fat32 and the other as ext4. Also how do I have this drive mount on boot? Right now I have it as a fat32 and it does not mount! I also need to know what would be a good tool for complete disk backup using a gui?

---

### Post by gldearman on 2009-08-21
Lots of questions there.  Here are answers for two:

To make a drive mount upon booting, you have to add a line referencing it to /etc/fstab.

I'm not going to try to go through the process of explaining what line you need to add, since I don't know anything about your drive.  But you can read [this page]("https://help.ubuntu.com/community/Fstab") to find out.

The way you mount the drive in fstab should affect who is allowed to read and write it as well, so that solves another problem.

---

### Post by abhilashm86 on 2009-08-21
use ntfs-3g config to automount your hard drives, open a terminal,
```
sudo apt-get install ntfs-config

```
then open that appplication,
```

sudo ntfs-config
```
now you enable the drives, i'll mount automatically during boot-up........

---

### Post by gldearman on 2009-08-21
OK, having re-read your post, I'm a bit confused.

You have two drives.

Drive #1 has two partitions.  One is Ubuntu /, the other is Ubuntu home.

Drive #2 is one partition, ext4.

You have deleted your previous Windows installation.

Is all that right?

So, what FAT32 drive are you having trouble with?  And what Windows installation do you need to share drives with?

While Windows cannot natively access ext4 partitions, there are programs that allow you to read (and even write to) ext2/ext3 partitions from Windows.  So, if all you want is access to your files from Windows, that's an option.  You can learn more about some of these programs [here]("http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html").

If you need Windows to have more access than that to a partition shared with Ubuntu, I would advise using an NTFS filesystem.  Or, as you said, you can split the drive into NTFS and ext3.

---

### Post by mercules2178 on 2009-08-21
drive two is fat32, is it better for linux to use ext4?
Windows is now gone on this desktop, I have an acer laptop that will not install any version of linux, and i have movies and music that i will be sharing between the two! I just want to set my drives up to benefit my "os". Thanks for all the help!

---

### Post by gldearman on 2009-08-21
ext4 and ext3 are native Linux filesystems, so, yeah, Ubuntu will work better with them.  NTFS/FAT32 don't support Linux file permissions or other features.  Ubuntu *can* use FAT32 drives fine for storing data -- but you do lose these features.

Check out the ext3-reading software for Windows that I recommended.  If it will suit your needs, go with ext3.  Otherwise. leave it as FAT32, or reformat as NTFS.

I wouldn't bother with ext4 on a drive that is just going to be used for data.  It may make it harder to share with Windows in the long run, for minimal benefit.

---

