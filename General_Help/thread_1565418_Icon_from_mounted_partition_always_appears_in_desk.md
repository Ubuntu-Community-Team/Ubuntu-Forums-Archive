---
title: "Icon from mounted partition always appears in desktop"
date: 2010-08-31
forum: General Help
---

### Post by ressaw on 2010-08-31
Hi, I set my fstab to auto mount one of my partitions in ~/Music.
It works perfectly, but there is always the icon in the desktop pointing to my partition with the name "40 GB FileSystem". The idea behind mounting it automatically to ~./Music was for the partition to be transparent to me...
Is there a way to remove that icon from the desktop and from the Places menu?

---

### Post by alem189 on 2010-08-31
Open a terminal:

$gconf-editor

go to
apps > nautilus > desktop > volumes_visible (unselect) to remove *ALL* volume icons.

---

### Post by ressaw on 2010-08-31
> **alem189 said:**
> Open a terminal:

$gconf-editor

go to
apps > nautilus > desktop > volumes_visible (unselect) to remove *ALL* volume icons.

Thanks for the quick answer,

Does that affect network locations opened too?
It's just that icon that I don't want to see because is automounted every time I boot is there a way to just mark that one not to be shown?...

---

### Post by alem189 on 2010-09-01
Well, another thing I think would work is mounting the partition in /mnt, and the symbolically linking to ~/Music to it. But maybe that won't work. You may find more useful information in [_this thread_]("http://ubuntuforums.org/showthread.php?t=193470"), which I got my first post from.

---

### Post by hhh on 2010-09-01
> **ressaw said:**
> Does that affect network locations opened too?
It's just that icon that I don't want to see because is automounted every time I boot is there a way to just mark that one not to be shown?...
AFAIK that shouldn't affect networks, just removable volumes (USB drive, CD, DVD, etc...)

---

### Post by ressaw on 2010-09-01
Is there no other way? Just to disable THAT mounted partition not to show?

This is my fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sdb1       /home           ext4    defaults        0       2
/dev/sda5 /home/ressaw/Music ext4 defaults 0 2

As you can see, There are two hard drives. The one that is mounted in /home doesn't show in the desktop, only sda5. It makes no sense. Is there any difference between them?

---

### Post by hhh on 2010-09-01
Sorry, I have experience with multiple OSes on one drive, but no experience with one OS on multiple drives. I hope someone else can help you.

---

### Post by ressaw on 2010-09-06
Sorry to do this, but I think there should be an easy answer for this
*bump*

---

### Post by truant on 2010-09-08
I've just done this exact same thing for my Media partition.  The only fix I've found is to mount the partition in /mnt and symlink it from my home directory.  

My fstab (edited for clarity):

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       /home           ext4    defaults        0       2
/dev/sda6       /mnt/meeja     vfat    uid=1000,gid=1000,utf8        0       2
```

After editing that, I did:

```
~$ sudo umount /home/truant/Media
~$ sudo mkdir /mnt/meeja
~$ sudo chmod 777 /mnt/meeja
~$ sudo mount -a
```

To remove the old mount, create the new one, set it's permissions and mount the filesystem to it.

Then just:

```
~$ ln -s /mnt/meeja/ /home/truant/Media
```

To create the link in my home directory.  My media partition now doesn't show up on either my Desktop or Nautilus's sidebar.

Hope this helps.  Ask if anything is unclear.  :)

---

### Post by ressaw on 2010-09-08
Perfect. It works.
Thank you very much,

but just for the sake of knowledge, what is the difference between mounting to the directory it was before and mounting it to /mnt/xxxx

---

### Post by truant on 2010-09-09
Er, one shows up on your Desktop and the other doesn't? ;)

Not sure.  At a guess I'd say that nautilus is configured to ignore mounts made in /mnt/ but not other places.  /mnt/ is the "traditional" place to make permanent mounts, so it kinda makes sense that's the directory you'd opt to ignore as a developer.

Glad you got yours working though.

---

