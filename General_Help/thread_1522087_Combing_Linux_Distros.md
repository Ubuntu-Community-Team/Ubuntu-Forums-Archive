---
title: "Combing Linux Distros"
date: 2010-07-01
forum: General Help
---

### Post by Jonny87 on 2010-07-01
I'm wanting peoples advice on something so I though I'd make a post here where I can here from more experienced users. I'm thinking about installing another distro (i.e. PC Linux) along side of Ubuntu 10:04, however if I did I'd want them to share the same home folder (which is on a separate partition). In speaking to my tutor (who is an experienced Linux user), he told me that while it may be do able, I may get conflict issues between the two. Things like user ID's being different or the way that they both handle their desktop environments.

So my question is;
Has any body done this successfully or do they know how I could do it to make it work? And if so how?

I want to do this so that I can get use to and learn a different style of Linux. But I don't want to have more than one home folder. I want to have all my docs and photos etc in one place regardless of what distro I'm using at the time.

---

### Post by ajgreeny on 2010-07-01
You should make a separate partition for data, set it to mount at boot time, and then make links to all the Documents, Music, Videos, Photos etc etc folders in each distro to those in the data partition.

You can do this easily either in the terminal, or probably more easily by dragging the folders from the data partition to the other distro's homes with the mouse middle button, and choosing "Link here" from the menu that will appear.

---

### Post by atomizer on 2010-07-01
+1 ajgreeny

settings could mess up the system.
If you want your data being shared, make a seperate data partition to save your data

---

### Post by Jonny87 on 2010-07-01
> **ajgreeny said:**
> You should make a separate partition for data, set it to mount at boot time, and then make links to all the Documents, Music, Videos, Photos etc etc folders in each distro to those in the data partition.

You can do this easily either in the terminal, or probably more easily by dragging the folders from the data partition to the other distro's homes with the mouse middle button, and choosing "Link here" from the menu that will appear.
That's a good idea, Thanks. It's probably the easiest way of doing it. If I do that are there any other potential dramas that I'd be likely to run into?

---

### Post by WorMzy on 2010-07-01
I don't use links, but I use something similar (mount --bind), and I've never had any problems in the past few years I've been doing it.

There is one thing that you might want to bear in mind though: when using mount --bind (and possibly links) with the data partition being on a separate disk to your Ubuntu installation, file transfers from one bound folder to another will take a considerably longer time than file transfers from an original folder to another.

e.g. I have "Downloads" and "Deb files" in my home folder which have folders in /media/Terastore bound to them. If I move a file from ~/Downloads to ~/Deb files, it takes a lot longer than moving the same file from /media/Terastore/Downloads to /media/Terastore/Deb files. Despite the fact that the file is staying on the same partition on the same disk, Ubuntu (and other Linux OS') get tricked into thinking that the file is being moved across disks.

I hope this made sense. It might be a moot point any way, since I've never used links, so it might not affect them the same way.

---

### Post by oldfred on 2010-07-01
Some more detail on linking to a data partition.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by Jonny87 on 2010-07-01
> **WorMzy said:**
> I don't use links, but I use something similar (mount --bind), and I've never had any problems in the past few years I've been doing it.

There is one thing that you might want to bear in mind though: when using mount --bind (and possibly links) with the data partition being on a separate disk to your Ubuntu installation, file transfers from one bound folder to another will take a considerably longer time than file transfers from an original folder to another.

e.g. I have "Downloads" and "Deb files" in my home folder which have folders in /media/Terastore bound to them. If I move a file from ~/Downloads to ~/Deb files, it takes a lot longer than moving the same file from /media/Terastore/Downloads to /media/Terastore/Deb files. Despite the fact that the file is staying on the same partition on the same disk, Ubuntu (and other Linux OS') get tricked into thinking that the file is being moved across disks. and how would I go about "mount --bind"

I hope this made sense. It might be a moot point any way, since I've never used links, so it might not affect them the same way.
Thanks I'll bear that in mind. However, I'm wondering would that still happen if I went to the data partition and moved the file from the folder to folder instead of doing it from the home.

Also just a thought, would there be any difference in putting the data on a separate HDD altogether rather than a different partition? Would it still work the same way?

---

### Post by WorMzy on 2010-07-01
> I'm wondering would that still happen if I went to the data partition and moved the file from the folder to folder instead of doing it from the home.

No, moving a file from /media/Terastore/Downloads to /media/Terastore/Deb files happens almost instantaneously.

> Also just a thought, would there be any difference in putting the data on a separate HDD altogether rather than a different partition? Would it still work the same way?

That's what I'm doing. Terastore is a dedicated 1TB disk that I store all my data on, my OS' are on another 1TB disk. I don't know how it'd affect the transfer time if the data and OS partitions were on the same disk, though I expect it would be quicker.

---

### Post by Jonny87 on 2010-07-01
> **WorMzy said:**
> No, moving a file from /media/Terastore/Downloads to /media/Terastore/Deb files happens almost instantaneously.


That's what I'm doing. Terastore is a dedicated 1TB disk that I store all my data on, my OS' are on another 1TB disk. I don't know how it'd affect the transfer time if the data and OS partitions were on the same disk, though I expect it would be quicker.

Thanks. I know "oldfred" quoted some links for mounting and I have checked them out, but how did you set your's up "WorMzy"? You metioned something about "mount --bind" earlier.

I ask so that I can get as many ideas and go with what I think is best for me to do. plus I'm learning even more about Linux and its commands so I'm excited.

---

### Post by WorMzy on 2010-07-01
I've modified my fstab file (/etc/fstab) on all my OS's so that Terastore is mounted at boot, and then the respective folders are bound in their correct places:

```
# <file system>                           <mount point>             <type>      <options>                                <dump> <pass>
proc                                      /proc                     proc        defaults                                 0      0
UUID=af60c425-1def-43fa-a30e-28fc50ecd4ca /                         ext4        relatime,errors=remount-ro               0      1
UUID=1a79c868-55e9-44cf-a902-0a89cc3ad114 none                      swap        sw                                       0      0
/dev/scd0                                 /media/cdrom0             udf,iso9660 user,noauto,exec,utf8                    0      0
[B]UUID=7A5C94995C94522D                     /media/Terastore          ntfs        user,uid=1000,gid=1000,umask=002,exec,rw 0      0
/media/Terastore/Collection/              /home/wormzy/Collection   none        bind                                     0      0
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures     none        bind                                     0      0
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents    none        bind                                     0      0
/media/Terastore/Downloads/               /home/wormzy/Downloads    none        bind                                     0      0
/media/Terastore/Videos/                  /home/wormzy/Videos       none        bind                                     0      0
/media/Terastore/Deb\040files             /home/wormzy/Deb\040files none        bind                                     0      0[/B]

```

Happens every time, without fail, due to the UUID being used to identify Terastore (rather than major/minor identifiers like "/dev/sda2" which can change if disks are moved around/removed/added on a hardware level)

Don't be confused by the lengthy options for the Terastore entry, because it's an NTFS partition (so I can access it from Windows too), you have to set the owner, group and permissions at mount time, or not at all. I've set it so that I and "my group" (which is just me) own all the files on it (uid=1000,gid=1000), and everyone else can read and execute anything on it, but not modify anything (umask=002). Oh and the \040 is the escape character for a space, so fstab reads "\040" as " ".

---

### Post by Jonny87 on 2010-07-01
Ok thanks, that sounds pretty simple. couple more questions.

> you have to set the owner, group and permissions at mount time, or not at all.
Is that just with NTFS or any drve and can it be done for individual folder (i.e. if I have multiple users with their own folder)?

And if I set it up with each user, how could I change the fstab so that it would mount that users "new" home folder (the data partition) when they log in and not everyone when anyone logs in. If that makes sense.

---

### Post by WorMzy on 2010-07-01
Just NTFS (and most likely other non-Linux/Unix-like partition types), because it doesn't support Unix permissions. You have to set the permissions for the whole drive, and can't set/change the permissions on individual folders. If the data isn't sensitive, then you can just give everyone read, write and execute permissions on the entire drive, then bind each individual folder to their respective "owner"'s home.

If you want each users Documents folder (for example) to be private, and readable from Windows, then consider creating an ext2 (or ext3) partition to hold them all, then set the permissions accordingly, then create the fstab entries to bind them to the right places; there's a couple of ways of accessing ext2/3 from Windows. [Explore2fs]("http://www.chrysocome.net/explore2fs") is one of them, [Ext2IFS]("http://www.fs-driver.org/index.html") is another.

---

