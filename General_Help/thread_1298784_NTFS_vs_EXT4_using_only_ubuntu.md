---
title: "NTFS vs EXT4 using only ubuntu"
date: 2009-10-23
forum: General Help
---

### Post by Mawoon on 2009-10-23
I've been searching, but I still haven't find any response to my question which is;

What is the advantage or disadvantage of formatting an external hard drive (a 250gb 2.5inch portable drive) to ext4.

Bare in mind, I'm only using ubuntu, a 9.04 32bit on the school computers, and 9.10 64bit at home.

I'm using the hard drive especially to run 2 vmware images of windows 7 and ubuntu 9.04, at school we always run our ubuntu 9.04 once the pc is booted.

So what I'm really wondering is, will there be significant differences, in starting speed, copying speeds, etc. Will I have more advantages at home because 9.10 is ext4 by default, and 9.04 is ext3?

Thanks in advance

---

### Post by mike555 on 2009-10-23
Permissions is one consideration , also defraging isn't needed in EXT 4 ..........

---

### Post by lovinglinux on 2009-10-23
ext4 is faster

---

### Post by doomsword2001 on 2009-10-23
i've read a month ago that ext3 was a bit slower for copying big files

---

### Post by vinutux on 2009-10-23
EXT4 is far better than NTFS but EXT4 is not supported outside linux ....... Check this **[http://en.wikipedia.org/wiki/Ext4]("http://en.wikipedia.org/wiki/Ext4")**

**[There is comparison of file systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")**

---

### Post by az on 2009-10-23
NTFS-3G has performance issues when dealing with large files.  I would not store a VMware image on an NTFS filesystem in Ubuntu.

---

### Post by Giblet5 on 2009-10-23
As someone else stated, ext4 seems to be noticeably faster on large (eg, .vmdk) file transfers and it is supported by 9.04 systems.

NTFS is appropriate only for Microsoft Windows systems. NTFS is a good filesystem but it lacks the finer access controls of Unix filesystems (any of them). That bites a lot of Ubuntu users as you can easily see from some of the past posts in this thread.

NTFS fragments files across the disk, requiring additional periodic maintenance. If you sit around twiddling your thumbs most of every day, that won't be a problem. Sitting and staring at PerfectDisk, by Raxco, is a delightful pastime. ;)

NTFS file ops on larger files is measurably slower than ext3 or ext4, even when comparing the rates under Windows v Linux.

Large external NTFS drives, which *should be* most useful for Windows systems, don't always work with Windows. I did some testing for someone yesterday because his Win7 install couldn't write to a 320GB external NTFS filesystem.

*My* conclusion: use ext3 or ext4. Ext3 is slightly more portable than ext4 and performs very very well.

---

### Post by alphaniner on 2009-10-23
ext* also fragments.  It is designed to *prevent* fragmentation, but that doesn't mean it completely avoids it.

Regardless, the ext* filesystems are vastly superior to NTFS.  If you don't need to directly connect the storage device to Windows machines (you can always share over the network regardless of the filesystem), go with a Linux filesystem.

---

### Post by RaveJunkie on 2009-10-23
EXT4 is better.  I am running 9.04 on a few machines and on one i timed a load on ext3 then formated and went to ext4 and then booted and cut off a few seconds on boot.  That is on a quad boot machine and my 6 meadia drives are all ntfs and i can read and write to them no problem (all four OS share pictures, music ect)  plus my liniux drive never needs a defrage and the read write times are faster


[http://www.hiprank.com/ext3-vs-ext4-vs-jfs-vs-ntfs-vs-reiserfs-vs-vfat-vs-xfs.html](http://www.hiprank.com/ext3-vs-ext4-vs-jfs-vs-ntfs-vs-reiserfs-vs-vfat-vs-xfs.html)

---

### Post by P4man on 2009-10-23
There is very simple reason not to use ntfs if you dont have a windows machine; the day the volume gets removed without synching first, you;ll have a bloody hard time accessing it again. The only safe and recommended way is to connect it to a windows machine, boot it, and shut it down again.

Now you can check it in linux and/or force the mount but its definately NOT a good idea. Hencem with no windows nearby, stick to linux native filesystems.

---

### Post by kimda on 2009-10-23
I would use ext3/4. And install ext3 program on Windows to access it under Windows.

---

### Post by XCan on 2009-10-23
I think the permission issue as mentioned needs to be highlighted as well. All your text files will look like they've executable flag, for example, kind of annoying.

---

