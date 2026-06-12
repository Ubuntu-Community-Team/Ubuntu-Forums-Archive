---
title: "missing 15% of disk capacity"
date: 2010-09-06
forum: General Help
---

### Post by mkaut on 2010-09-06
Hello,

I have a 650 GB ext3 LVM partition with RAID 1 on. The partition is 85% full, but the system says "no space left on device" - where did the 15% go?

I ran "tune2fs -m 0 /dev/mda1", so it is not the space reserved for the root - so Nautilus reports the same free capacity as GParted now.

Some more info:
- Ubuntu 9.10 x64
- GParted says 650 GiB, 104.83 GiB free
- Nautilus says 104.8 GiB free
- The system thinks the disk is completely full - I cannot even create (touch) a new empty file

Hope someone can help me find mine 100 GB..

Michal

---

### Post by srs5694 on 2010-09-06
Please post the output of "df -h", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by mkaut on 2010-09-06
> **srs5694 said:**
> Please post the output of "df -h", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

Thanks for the quick response. Here is the output:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              22G  9,3G   12G  45% /
udev                  2,0G  440K  2,0G   1% /dev
none                  2,0G  376K  2,0G   1% /dev/shm
none                  2,0G  344K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/sda1             236M  149M   75M  67% /boot
/dev/sda9             3,4G  693M  2,5G  22% /var
/dev/md0               20G   12G  6,9G  64% /home
/dev/md1              650G  545G  105G  84% /data

```
I am talking about the /data partition.

I actually deleted a bit over 100 MB now, so the use is 84% instead of 85% as in the orig. post. After that, I could write to the disk for a little while, but now it again says "no space left" :(

---

### Post by Rinzwind on 2010-09-06
Did you check /data/.Trash-1000/
If you deleted files as root they will not be deleted when you empty trash from gnome panel ;)

---

### Post by srs5694 on 2010-09-06
Given the df output, it's not likely to be files in a trash folder, although it won't hurt to check.

I recommend unmounting the partition and then running an e2fsck on it, as in "sudo e2fsck -f /dev/md1". (If it's not an ext2/ext3/ext4 filesystem, use fsck or a fileystem-specific fsck variant; however, since you say you used tune2fs, it sounds like it's an ext2/ext3/ext4 filesystem.)

---

### Post by gmargo on 2010-09-06
Could you have run out of inodes?  Try a "df -i".

---

### Post by mkaut on 2010-09-06
> **gmargo said:**
> Could you have run out of inodes?  Try a "df -i".

That was it (I think)! Thanks.
```

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/md1              665600  665600       0  100% /data

```

Now, what can I do?

Michal

---

### Post by HermanAB on 2010-09-06
Hmm, note that Ext3 reserves a huge space for the journal - about 7%, or about half of your missing space.  If you want a more efficient file system, use JFS or XFS.  Both of those use only about 0.5% for their journals and are therefore tremendously more efficient regarding disk space.

---

### Post by DogMatix on 2010-09-06
This might help: [Running out of inodes problem]("http://www.gossamer-threads.com/lists/netapp/toasters/7148")

---

### Post by mkaut on 2010-09-07
> **DogMatix said:**
> This might help: [Running out of inodes problem]("http://www.gossamer-threads.com/lists/netapp/toasters/7148")

Thanks - but I don't think it helps - they use "maxfiles command" which I don't have .. it is not even sure they speak about Linux, let alone ext3.

So I just repeat the question: can I increase the number of inodes on an ext3 partition on Ubuntu, without losing the data?

Thanks.

---

### Post by mkaut on 2010-09-07
It looks one cannot change the number of inodes on an ext3 partition, so I will have to reformat. Can someone check my battle plan and fill in the blanks, please?

1. unmount the /dev/md1 drive + remove the raid (needed?, if so, how?)

2. mount /dev/sda8 (raid drive 1) and format it

3. mount /dev/sdb7 (raid drive 2) and all data from to /dev/sda8

4. format /dev/sdb7 in the same way as /dev/sda8 (needed?)

5. unmount the two drives (?)

4. create a new raid using the two drives - do I need to say which disk I want to mirrored, or will it figure out automatically?

ps1: Where does the file format "live", on /dev/sd*, or on /dev/md1?
ps2: With the danger of starting a flame war, what fs should I use for the data partition (650GB, most files about 1-10 MB (photos and music))?

Thanks

---

### Post by scouser73 on 2010-09-07
Hopefully this will be able to explain to you about missing disk space: [http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

---

### Post by gmargo on 2010-09-07
> **mkaut said:**
> 
ps1: Where does the file format "live", on /dev/sd*, or on /dev/md1?


The ext3 filesystem lives above the RAID layer.  You'll be running mke2fs on /dev/md1, not the /dev/sd* drives, so there's no need to un-RAID, format, and re-RAID the two devices.

---

### Post by mkaut on 2010-09-07
> **gmargo said:**
> The ext3 filesystem lives above the RAID layer.  You'll be running mke2fs on /dev/md1, not the /dev/sd* drives, so there's no need to un-RAID, format, and re-RAID the two devices.

Thanks for info.

The question is, if I don't un-RAID the array, how do I save the data? I do not have any other disk to use as a backup - that's why I wanted to re-format one of the disks (with more inodes), copy the data there and then somehow (this is the step I need help with) create an RAID-1 array by making the second disk a mirror of the first one ... is it even possible, if the file system lives on the RAID, i.e. can data on a disk survive creation of a RAID-1 array?

Michal

---

### Post by gmargo on 2010-09-07
I understand now.  I think you can do this by removing (logically not physically) one of the drives from the raid array, and then creating a new raid 1 array with the removed drive.  So you'd have two raid 1 arrays, /dev/md1 and /dev/md2, each with only a single drive.  Then format /dev/md2 with the increased inodes, copy files over, then destroy /dev/md1 and move that drive to the second raid array and let it sync up.  I'm not sure how LVM affects all this though.

BTW, this would be good use for a virtual machine - you can test the whole procedure without risking anything.

---

### Post by srs5694 on 2010-09-07
Stepping back a bit, the usual cause of running out of inodes is that you've got a large number of very small files. If the function of the disk is to store such files, then there's not much you can do to avoid this fact; however, if the files are temporary files, small log files, or whatnot, then you might be able to at least buy yourself some breathing room by deleting those files. Once they're gone, their inodes will be freed for re-use.

Another factor: Ext2/3/4 uses a fixed number of inodes. You can set the number of inodes when you create the filesystem, so if you stick with ext2/3/4, you'll need to use the -i or -N option to adjust the number of inodes on the new filesystem. Alternatively, you can use a filesystem that does not nail down the number of inodes at filesystem creation time, such as ReiserFS. (I believe Btrfs is also flexible in this respect.) ReiserFS also has the advantage of packing in more small files per MB than most other filesystems, so if you're storing lots of small files, ReiserFS is a good choice.

---

### Post by mkaut on 2010-09-07
> **srs5694 said:**
> Stepping back a bit, the usual cause of running out of inodes is that you've got a large number of very small files. If the function of the disk is to store such files, then there's not much you can do to avoid this fact; however, if the files are temporary files, small log files, or whatnot, then you might be able to at least buy yourself some breathing room by deleting those files. Once they're gone, their inodes will be freed for re-use.

Another factor: Ext2/3/4 uses a fixed number of inodes. You can set the number of inodes when you create the filesystem, so if you stick with ext2/3/4, you'll need to use the -i or -N option to adjust the number of inodes on the new filesystem. Alternatively, you can use a filesystem that does not nail down the number of inodes at filesystem creation time, such as ReiserFS. (I believe Btrfs is also flexible in this respect.) ReiserFS also has the advantage of packing in more small files per MB than most other filesystems, so if you're storing lots of small files, ReiserFS is a good choice.

Thanks.

I think I will try to do this, as re-formatting sounds like a bit risky job. Is there some good way to find the small find, like searching for directories with a lot of files/inodes?

Michal

---

### Post by btindie on 2010-09-07
As suggested previously I think your best option would be to break the RAID 1 mirror, creating a degrated RAID array by removing the second disk from it then creating a normal disk and copying the contents of the degraded mirror to it.
 
Format the original degraded RAID 1 mirror with a file system of your choice, increasing the inode count to a suitable level if using Ext3 and copy the contents of the separate disk to the new RAID array. Once done, add the separate disk to the new RAID array. It may take a while for it to rebuild. It should then be good to go.
 
You could use the find command to see how many small files you have and if they're a lot then you could lower the bytes-per-inode count(mke2fs -i). [http://linux.die.net/man/8/mke2fs](http://linux.die.net/man/8/mke2fs)
 
Also, as mentioned previously, you can test this method under VirtualBox/KVM.

---

