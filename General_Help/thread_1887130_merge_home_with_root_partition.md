---
title: "merge home with root partition"
date: 2011-11-26
forum: General Help
---

### Post by linuxcss on 2011-11-26
due to small disk size I'd like to merge my home partition into root partition
and then remove the partition that used to house home

how do i do the merge?

---

### Post by JKyleOKC on 2011-11-26
While it's possible to do what you ask, it's a bit risky -- and it won't save you anything at all in the way of disk space. In fact, it will use quite a bit MORE space during the time that you are doing the merge, since it will be necessary to copy every bit of material stored in your current home directory and all of its subdirectories into a duplicate in order to do the merge.

If you run out of disk space while doing this, you can lose part or all of your files. It's a high-risk operation.

The reason that eliminating a separate partition won't save you any space is that each partition's entry in the partition table is only 16 bytes long, and the size of the table doesn't change at all if all 16 are blank -- it's fixed at a total of 64 bytes and that won't change. If you have an "extended partition" that will take up an additional 4,096 bytes of disk space, but once such a partition exists it would have to be totally removed to reclaim that space. A normal installation of Ubuntu does create such a partition, in order to make room for any reasonable number of partitions you might want, but it also installs critical system components there, making it almost impossible to delete without destroying your entire installation. It can be done, but is hardly worth the effort since you'll only reclaim so little space by doing so.

If you're running out of space, your best bet is to clean out the automatically-archived package files and logs. Take a look at the files in /var/log; it's safe to remove any of those with names ending in ".gz" since they are archives of previous activity, and this alone can save you a few megabytes of disk space.

---

### Post by drs305 on 2011-11-26
I agree with JKyleOKC. Unless your HOME folder is on another drive and you want to make space on *that* drive, it isn't going to help a lot.

If you still want instructions on how to do it I will provide a way, but again, there is always the chance of messing things up.

---

### Post by Lars Noodén on 2011-11-26
> **JKyleOKC said:**
> ...If you're running out of space, your best bet is to clean out the automatically-archived package files ...

You can clean out the cached package files with apt-get:

```

sudo apt-get clean

```

---

### Post by lswb on 2011-11-26
It may well be the case for the OP that doing away with a separate /home partition WILL yield a lot more useable space. Suppose for example he originally set up his system with a 10GB root and a 10GB /home. Maybe his / partition is 70/80% full but his /home is only 10%. Merging the 2 partitions and using a /home directory instead would free that much space up for installing new applications and other purposes. 

That said, I would recommend a full backup before doing any partition editing, or at the very least, backup all personal data. If your /home/user directory contents will fit on a USB stick, that would be an easy way to do it. You will need to research using gparted or similar partition editor for the specific steps needed to combine the 2 partitions.

I cannot give specific or comprehensive instructions, but here's the basics. You should not do this until you are comfortable with your understanding of what you are doing and the specifics of your own system. 

Most likely your current home partition is mounted at the /home directory on the root partition. Check /etc/fstab. If you have room enough now, you can boot a live CD and simply copy your (separate partition) ~/user directory contents to  /home/user on the root partiotion. If there is not enough room you will need to use a USB stick or other intermediate step to save your ~/user files. Remember you will need to do a full recursive copy including all subdirectories and hidden files; research the command line options to the "cp" command. Then while still running the live CD, edit /etc/fstab on the hard drive and comment out or remove the line that mounts the home partition to /home. Use gparted to combine the 2 partitions (This is where problems can occur that make a backup a really good idea before starting). If all goes well, when you next reboot from the hard drive, everything will "just work" Again this is not meant to be comprehensive description of the process, just an overview. There are many websites, forums and other resources where you can (and should) look for more details.

---

### Post by linuxcss on 2011-11-28
"It may well be the case for the OP that doing away with a separate /home partition WILL yield a lot more useable space."

thanks all and lswb comment is why I want to do it.
Need some slop space for install apps that is in a common pool, 1 partition and not segmented between 2.

Looks like I need to comment out the fstab entry that  mounts home, save home off to external media,
remove home partition, then size root partition to desired size, and then copy home to root

---

### Post by JKyleOKC on 2011-11-28
> **linuxcss said:**
> Looks like I need to comment out the fstab entry that  mounts home, save home off to external media, remove home partition, then size root partition to desired size, and then copy home to rootBasically that's it, but I would save home off to external media before modifying fstab. After modifying fstab, restart the system before attempting to restore the home content, and modify the partitions to merge them. Then restart a second time, and the actual home directory for you should still exist in the root filesystem, allowing you to log in normally and still have whatever configuration data was put there on the original installation, so you should only need to copy the content of your home directory back to it, overwriting anything that is already there.

If /home does not contain a home folder for you, then you'll need to get to a GRUB menu and select recovery mode so that you can log in as root (automatically, no need for a password) and copy the whole content of your saved external media to it, then restart a final time.

Good luck!

---

