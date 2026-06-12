---
title: "ext3 question"
date: 2010-04-03
forum: General Help
---

### Post by new_tolinux on 2010-04-03
I read this on Wikipedia:
> Since ext3 aims to be [backwards compatible]("http://en.wikipedia.org/wiki/Backwards_compatible")  with the earlier ext2, many of the on-disk structures are similar to  those of ext2. Because of that, ext3 lacks a number of features of more  recent designs, such as [extents]("http://en.wikipedia.org/wiki/Extent_%28file_systems%29"), dynamic allocation of [inodes]("http://en.wikipedia.org/wiki/Inode"), and [block suballocation]("http://en.wikipedia.org/wiki/Block_suballocation").[[12]]("http://en.wikipedia.org/wiki/Ext3#cite_note-12")  There is a limit of 31998 sub-directories per one directory, stemming  from its limit of 32000 links per inode.[[13]]("http://en.wikipedia.org/wiki/Ext3#cite_note-13")Source: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
The only thing is that I'm a little bit confused.

Does this mean: /somedir/a/ and /somedir/b/ can not have more than 32000 sub-directories together, so let's say if /somedir/a/ has 20000 sub-directories, then /somedir/b/ is limited to 12000 sub-directories

Or does it mean: /somedir/a/ can hold 32000 sub-directories and /somedir/b/ can hold 32000 subdirectories at the same time.

---

### Post by warfacegod on 2010-04-03
I have no idea how to answer your question. I simply ask why not use ext4?

---

### Post by new_tolinux on 2010-04-03
First of all 9.04 has ext3 as the default filesystem.
What I read in some topics on this forum ext4 did not prove itself completely yet and there are some stability-issues, although it has been implemented as the default filesystem in 9.10 if I'm correct.

Edit:
By the way, it's not that I'm planning on creating 32000 sub-directories in 1 folder, but Ubuntu has a lot of subfolders, so I guess it's likely that somewhere I could run into that 32000 limit.

---

### Post by 98cwitr on 2010-04-03
im using ext3 as well. I want the bugs out of ext4...plus, what is the REAL advantage? I havent found one.

---

### Post by warfacegod on 2010-04-03
new_tolinux:

I've been using ext4 since its release and I've had zero issues with it. Yes, its default for 9.10 it is an option for 9.04 during install. Extremely unlikely you'll ever hit 32,000. *Possibly* if you were running a Server.

98cwitr:

I have seen moderate to serious performance increases from ext3 to 4 in every system I have switched to ext4.

---

### Post by 98cwitr on 2010-04-03
o'rly? That's cool. I've seen the instructions on converting without having to wipe the OS, but Im too much of a chickenshit to try it...haha. Ill wait for the bugs to get worked out.

---

### Post by new_tolinux on 2010-04-03
I do actually run a development-server on a Gnome-based install for which I used the alternate 9.04 CD.
Maybe that's not the best solution, but it works best for me because I sometimes need to use the machine (it's also my laptop).
Upgrading to 9.10 did not satisfy me at all (lots of driver issues on that laptop).

I don't have any problems yet, but I'm just curious about the limitations of ext3.

---

### Post by geirha on 2010-04-03
A safe way to try it out; create a relatively small file (like 20MiB), format it with ext3, mount it, and see how many directories you manage to create ;)
```

mkdir -pv /tmp/teststuff/mnt
cd /tmp/teststuff
dd if=/dev/zero bs=1M count=20 of=file.img
mkfs.ext3 file.img
sudo mount -v -o loop file.img mnt/

# Now, see what happens if you create 32k directories in a/ and b/
cd mnt
mkdir -v a b
cd a
echo {1..32000} | xargs mkdir
cd ../b
echo {1..32000} | xargs mkdir

# clean up
cd /tmp/teststuff
sudo umount -v mnt/
rmdir -v mnt/
rm -v file.img

```

---

### Post by kblft on 2010-04-03
If the wikipedia entry is correct then it means 32000 per inode - which means that every directory can have 32000 directories under it, not that there are 32000 altogether.

---

### Post by srs5694 on 2010-04-03
kblft is correct; the limit is on a per-subdirectory basis. You can have more than 32,000 subdirectories in a filesystem, just not in a single subdirectory. I did some tests on this recently.

As to advantages of ext4fs, one set relate to very big hard disks. You can create larger filesystems (that is, filesystems that fill larger partitions or logical volumes) with ext4fs, and you can create larger files with ext4fs. The limits for ext3fs are larger than you can exceed on a single physical disk, though, so this really is only an issue for big servers. Another advantage of ext4fs is that it improves performance, particularly in areas in which ext3fs has often lagged. For instance, if you've got a big file (with a size measured in the gigabytes, say) and delete it, it will take ext3fs a while to do the job. If you do this with ext4fs, it'll be much faster. There are some other advantages, but they're mostly very esoteric issues.

Overall and IMHO, the advantages of ext4fs are minor enough that most desktop installations don't really need it. The one situation where I'd say it might be worthwhile for typical readers of this forum is if you're using Ubuntu as a multimedia system (a MythTV box, say). In that case, ext4fs's superior handling of large files makes it worthwhile; however, JFS and XFS offer similar advantages in that case, and they're both better tested than ext4fs. Therefore, I personally prefer either (or especially XFS, which seems more stable to me) over ext4fs, which as other have pointed out, has seen some problem reports. This may change in time, however; I expect ext4fs will be more reliable in 6-12 months. Beyond that, Btrfs is likely to become the "top dog" among Linux filesystems. At the moment, though, Btrfs is even newer than ext4fs, and I wouldn't trust Btrfs with valuable data.

---

### Post by kblft on 2010-04-03
I tend to agree with srs5694 - I've been working with ext4 for a while now, and the only noticeable advantage to ext3 (other than its handling of larger files) is the fact that fsck is much faster on ext4 - otherwise its pretty much the same...

---

### Post by new_tolinux on 2010-04-03
> **geirha said:**
> A safe way to try it out; create a relatively small file (like 20MiB), format it with ext3, mount it, and see how many directories you manage to create ;)
I did try on a VM, and I only managed to produce 5123 subdirectories in a/ before it said: ```
mkdir: cannot create directory `xxxxx': No space left on device
```> **srs5694 said:**
> kblft is correct; the limit is on a per-subdirectory basis. You can have more than 32,000 subdirectories in a filesystem, just not in a single subdirectory. I did some tests on this recently.
That seems to contradict with the results I've got from geirha's code? Any ideas why?
> **srs5694 said:**
> I expect ext4fs will be more reliable in 6-12 months. Beyond that, Btrfs is likely to become the "top dog" among Linux filesystems. At the moment, though, Btrfs is even newer than ext4fs, and I wouldn't trust Btrfs with valuable data.
At the moment I think "ext3" still works for me. Although data on my development server isn't really that valueable, I like my machine to be stable. So if I don't need to change to another (less reliable) filesystem I prefer not to change. Thanks for the information anyway.

Edit:
I tried it again (same VM) but this time in the "real" filesystem.
I created /tmp/a/ and /tmp/b/ and /tmp/c/ and ran this command in all three dirs:
```
echo {1..32000} | xargs mkdir
```This time it only came up with an error on 31999 and 32000 (seems correct, see #1: "_There is a limit of 31998 sub-directories _per one directory, stemming   from its limit of 32000 links per inode.")
My best guess is that 20MB just is not enough to store that amount of directories.

I'm marking this thread as "Solved", everyone thanks for the directions.

---

### Post by srs5694 on 2010-04-03
> **new_tolinux said:**
> I did try on a VM, and I only managed to produce 5123 subdirectories in a/ before it said: ```
mkdir: cannot create directory `xxxxx': No space left on device
```That seems to contradict with the results I've got from geirha's code? Any ideas why?

Because you ran out of disk space. Either you created an extremely tiny logical volume for testing or you were creating files with contents in your directories. I did my testing on a 16GB USB flash drive, so I didn't have problems with it running out of space. When I did run into the ext2/ext3 limits, the error message was something about an inability to create links (I don't recall the precise wording), not "no space left on device."

---

### Post by new_tolinux on 2010-04-03
> **srs5694 said:**
> Because you ran out of disk space. Either you created an extremely tiny logical volume for testing or you were creating files with contents in your directories. I did my testing on a 16GB USB flash drive, so I didn't have problems with it running out of space. When I did run into the ext2/ext3 limits, the error message was something about an inability to create links (I don't recall the precise wording), not "no space left on device."
The code from geirha specified to create a virtual disk from 20 MB.
For the error-code, it's this (still had it on my screen) :
```
mkdir: cannot create directory `31999': Too many links
```.

But again, thanks for helping me to solve it.

---

