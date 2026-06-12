---
title: "help with etc/fstab"
date: 2009-09-29
forum: General Help
---

### Post by cagliostro on 2009-09-29
I'd like to be able to read and write to my data partitions, in this case Windows D: and E: which are vfat partitions. I worked on this all weekend. Here is the etc/fstab I finally created:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a9a4bf60-f3dd-43b9-983e-a1b0570e1dd1  /  ext3   relatime,errors=remount-ro 	0       1

# /dev/sda7
UUID=9f84e870-e182-4e70-9406-e1c52ab7502f	none	swap	sw	0       0

[B]# /dev/sda3
LABEL=WIN_D	/media/sda3	vfat	user,noauto,uid=david,dmask=027,fmask=137	0	0

# /dev/sda5
LABEL=Puppy_hda5 /media/sda5	ext3	user,noauto,rw		0	0

# /dev/sda10
LABEL=WIN_E	/media/sda10	vfat	user,noauto,uid=david,dmask=027,fmask=137	0	0[/B]

# CD/DVD
/dev/scd0       /media/cdrom0   udf,iso9660	user,noauto,exec,utf8	0       0


I created the entries for sda3, sda5, and sda10. First I created mount points: sudo mkdir /media/sda{3,5,10}

UUID has caused a lot of trouble for me in the past as it changes with a new install into a partition. I read that using /dev/sda3 has problems as it can also change. So I labeled the partitions, and used the labels in etc/fstab.

I read that ownership and permissions for a vfat partition are determined on mount, so for /dev/sda3 (WIN_D) I used the above options. I want ownership of this partition, to be able to read and write to it. This appears to work. In this partition, sda3, I can right click on files, and can delete them. So maybe sda3 is successful.

But the entry for the other vfat partition (WIN_E) sda10 is identical. Here I do NOT have read/write access. If I right click on files, actions such as cut or delete are grayed out. **So why does fstab work for /sda3 but not for /sda10?**

Note that sda3 is a primary partition, but sda10 is in the extended partition that includes various Linux partitions. I can't see why this would affect fstab.

I thought the above would give read/write access to Puppy on /sda5, but it doesn't. I mounted this partition, then used in terminal:
sudo chown david /media/sda5
sudo chmod 644 /media/sda5
[oops, that doesn't work, can't see any of the files any more, totally gone--so use]
sudo chmod 777 /media/sda5
Now I can see the files in sda5 again, but still have no write access.

I tried to unmount each of these partitions, but am told I don't have the right to do so. This really isn't what I want.**[B][B]**[/B][/B]

---

### Post by undecim on 2009-09-29
You shouldn't need to mess around with fstab to access addtional drives/partitions. Just go to your "Places" menu and select the drive. It should mount such that you can access it. (although your current fstab entries may interfere with that.)

---

### Post by cagliostro on 2009-09-29
I don't understand your reply.

Are you talking about using "Computer" to click on the partition?

The mount point for these partitions is missing. I had to add them manually to /media. In any case I would have to become root. One can type in terminal "gksu nautilus" which is I guess what you're alluding to. Then any file manipulation means that it is owned by root.

---

### Post by oldfred on 2009-09-29
You need to use fstab if you want to permanent mount the directories.

These are my entries that work for a fat and ext3 partitions:

# Entry for /dev/sda4 :
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /home/fred/data ext3 auto,users,rw,relatime 0 2

I found that  (below), so all I really need is realtime without the auto,users,rw
# The fourth field, (fs_mntops), describes the mount options associated with the filesystem.
defaults = rw, suid, dev, exec, auto, nouser and async

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

---

### Post by cagliostro on 2009-09-29
Interesting, you're mounting these under /home rather than in /media. Maybe that gets around the root ownership, and lets you operate as user. I'm not sure that these partitions will display in Computer if they're not in /media, so I will switch over to "auto" as you have done (instead of "noauto").

I'll experiment with this. Though I wish I knew why sda3 seems to works in fstab for me, but the identical entry for sda10 fails.

---

### Post by StuartN on 2009-09-29
> **cagliostro said:**
> But the entry for the other vfat partition (WIN_E) sda10 is identical. Here I do NOT have read/write access.

I do not see anything different with the fstab. Have you **ls -al /media** to check the ownership and permissions? And you could add uid=Fred to the options.

---

### Post by oldfred on 2009-09-29
I went back to check mine and this is my share

drwxrwxrwx  15 root root     16384 1969-12-31 18:00 share

It is root but everyone has permissions to do everything.

---

### Post by cagliostro on 2009-09-29
**SOLVED,**, I think. (Ownership and permissions.)

Make the mount points: sudo mkdir /media/sda{3,5,10}

Then, the steps I omitted:

sudo chown david:david /media/sda{3,5,10}
sudo chmod 777 /media/sda{3,5,10}

[I mistakenly thought this should be done after everything was mounted.]

Now both WIN_D and WIN_E work as expected; dmask=027, directory executable, fmask=137 files are read/write, but not executable since these are Windows vfat partitions. I was able to rename, edit, and delete files. I checked permissions and files are not executable.

Now when I click on the Puppy partition I see that everything is locked (little lock icons). Of course it is. Puppy operates in root mode. So I can extract downloaded files from Puppy, which is really all I wanted from this partition. Slightly modified the /etc/fstab entry:

# /dev/sda5
LABEL=Puppy_hda5 /media/sda5	ext3	relatime,users,noauto		0	0

Thanks for suggestions.

---

### Post by Iowan on 2009-09-29
Does [this]("http://ubuntuforums.org/showthread.php?&t=283131") fstab How-to help? Perhaps you've already seen it.

---

