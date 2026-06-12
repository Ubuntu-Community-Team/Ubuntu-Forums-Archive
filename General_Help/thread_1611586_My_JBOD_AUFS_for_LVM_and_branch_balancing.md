---
title: "My JBOD: AUFS for LVM and branch balancing?"
date: 2010-11-02
forum: General Help
---

### Post by Redsandro on 2010-11-02
I know, the title doesn't make sense in many ways, but this trick is neat and I think not enough people know it's possible. Considering it's SO EASY, easier then setting up LVM, more people should know about it to give **aufs** the attention it deserves. ;)

Everybody ends up with some **old hard disk drives**. Some are too small and upgraded in your workstation. Others are starting to get unreliable (SMART warnings).
An unreliable drive could work perfectly for another year, but you don't want your important data on it. However, storage is very useful in this media recording era, and media is not as important as your other files.

So if you, like me, stick all your old and unreliable drives in your Media Center, wouldn't it be nice to **have them all available under a single mount point**? It makes downloading, recording, target assignment and media storage assignment (inside the player) much easier.

First, I started using non-striped LVM (Logical Volume Management) for that. Seems like a good idea. A single mount point for all my stuff. But what the.. it turns out that even without striping, if one disk fails, **the entire LVM volume becomes unavailable and broken!** Of course, when a drive dies, the media dies with it. But that's no reason to loose all the media on the other drives that are perfectly fine!

So now I am migrating my LVM media to AUFS (Another Union File System). This is like Union File System, but better. Mounted drives (branches) are branched together under a single mount point, and it automatically uses all branches when storing data. You can do exactly the trick I was supposed to do, but now **a failing drive won't affect what's stored on the other drives**.

For this, you can use built-in aufs like so:
**mount -t aufs -o dirs=/mnt/disk1=rw:/mnt/disk2=rw:/mnt/disk3=rw aufs /mnt/aufs**
Where **disk1**, **disk2** and **disk3** are mounted /dev/sdxx partitions you want to use, and **/mnt/aufs** is the target branch.
You can put this in **/etc/fstab** like so:
**none /mnt/aufs aufs dirs=/mnt/disk1=rw:/mnt/disk2=rw:/mnt/disk3=rw 0 0** [COLOR="DarkGreen"](tested, works)[/COLOR]
Be sure the proper drives are mounted first!

This way, it reads from all branches at the same time. For writing, it fills the first branch until full, then it continues on the next one and so on.

Nice, eh?

[SIZE="4"]But wait, **I also have some questions myself!**[/SIZE]

Aufs can do branch balancing. Storing each file on the branch that has the most free space at the time. This is convenient, when a drive dies, it doesn't have a bad luck chance of holding all the data while an empty disk survives.
How do I do this? I can find very little relevant documentation on aufs.

I have two reliable and two unreliable small disks. It would be cool to fill the reliable two up first, and when they are full, start branch-balancing between the two unreliable disks. Is thos possible?

---

### Post by darkstar62 on 2011-02-21
I actually do this at home with my media center.  I have about 3 or 4 drives that I store content on, and merge them into one mountpoint with AUFS.

You can activate the branch balancing with the 'create=' mount option.  I use 'mfs', which is "Most Free Space" -- that is, it'll create new files on whichever drive has the most free space.  You can do round-robbin, and other things too.

This page has some good documentation:
[http://aufs.sourceforge.net/aufs.html](http://aufs.sourceforge.net/aufs.html)

Look down at the 'Policies for Creation' subsection under 'Policies to Select One among Multiple Writable Branches' for all the available create options.

---

### Post by Redsandro on 2011-02-21
Thanks, I found it out already, forgot to update the topic.
Remember to always constrain possibilities with an example! Here's mine:

(note: this is a MOUNT line)
```
none  /red  aufs  br=/mnt/red400=rw:/mnt/red300=rw:/mnt/red200=rw:/mnt/red160=rw,create=mfs,cpup=bup,auto  0 0
```

**Problem 1**: It doesn't work on boot, wtf

**Solution 1**: Edit **/etc/init.d/rc.local**, add:
```
#RED 2010/11/28 - umount and remount aufs because it fails on boot.
umount /red/
mount -a
```

No it doesn't make sense, but it does the trick.

Others brought **mhddfs** to my attention. Supposedly it is better:[list][*]Disk free information shows total, not just mfs drive
[*]NFS support
[*]Optimized for merging in stead of stacking
[*][http://romanrm.ru/en/mhddfs](http://romanrm.ru/en/mhddfs)[/list]

But I never checked or tried it. I invested too much time in understanding **aufs**, which it's not too straightforward and documentation is meager. But feel free to share your opinion and tell me which one is better!

---

### Post by darkstar62 on 2011-02-21
Hmm, interesting find.  I like that mhddfs will show you the combined free space of all drives.  I think I'll be sticking with aufs though, mainly because it supports dynamic adding/removing of branches without taking down the filesystem.  That's very useful to me so I can detach/unmount one drive, while other things are using the mount point.

Glad you found what you were looking for. :)

---

### Post by Redsandro on 2011-02-21
Hey I didn't know that one yet, what command can you use to unmount a single branch?

---

### Post by iwanovich on 2012-09-22
I used the same command:
mount -t aufs -o dirs=/mnt/disk1=rw:/mnt/disk2=rw:/mnt/disk3=rw aufs /mnt/aufs

On ubunu 12.04 (using sudo), but as soon as disk1 is full, it tells me there is not enough space in /mnt/aufs. Does your solution only work when mounted during boot with fstab? Have you encountered the same behavior?

---

### Post by Redsandro on 2012-09-24
I am currently not using AUFS because of different machine and one big drive so I cannot double-check, but I think I did not have that problem, as new files would be divided among branches.

Indeed, I had the AUFS running from fstab, but it has a different syntax. I looked in a backup image I took a while ago and it literally sais this:
```
none  /red  aufs  br=/mnt/red400p=rw:/mnt/red300p=rw:/mnt/red200=rw:/mnt/red160=rw,create=mfs,cpup=bup,auto  0 0
```
Also, I remember sometimes this would go offline immediately due to a bug or something, don't know if that's still valid, but for that I had this in my /etc/init.d/rc.local
```
#RED 2010/11/28 - umount and remount aufs because it fails sometimes.
umount /red/
mount -a
```
-edit-
Ah I see it sais the same lines of code in my post from a century ago haha, sorry for that.

---

