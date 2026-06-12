---
title: "Problems with ex partitioned drive."
date: 2010-08-14
forum: General Help
---

### Post by MacHaddock on 2010-08-14
Right so I reformated my windows partition to ext3. Now ubuntu tells me there is a problem with it when I start the system. It says it cand find it and asks me if I want to: s ignore this or m fix it manually. Well that or something quite similar.

Anyone got any Ideas about how I make it understan I don't have a windows partition any more?

---

### Post by lunix- on 2010-08-14
Strange, and never seen the problem my self.
Was the windowsdisk automounted in fstab before you repartitioned it and formatted it as ext3? 
If so, I would check to see if fstab contains some strange setting for your disk.  If this is not the problem, thn I have no idea :)   good luck

---

### Post by MacHaddock on 2010-08-21
this is what my fstab says:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=faf10530-010b-45de-96fa-b0d8fe7ff8f5 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=1bd5ff52-53f2-482b-bd90-a22631760252 /home           ext3    relatime        0       2
# /windows was on /dev/sda1 during installation
UUID=326CEB516CEB0F03 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=5b2b405d-b7e8-4364-9959-b42111c99904 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

And I bassicaly don't know what to make of that.

How do I stop Ubuntu locking for /windows and find my new partition instead.

---

### Post by MacHaddock on 2010-08-23
So here is how I solved my problem:

In my terminal: ```
sudo gedit /etc/fstab
``` (i think that's the right path)
Then in the fstab file I commented out (put a # in front  of): ```
UUID=326CEB516CEB0F03 /windows        ntfs     defaults,nls=utf8,umask=007,gid=46 0       0
```That stopped Ubuntu from looking for the non existing /windows partition.

Then I used: ```
sudo chown username:username /media/newfst3partition
``` to get that one to work properly.

Weee I'm a hacker \\:D/

Please feel free to leave a comment here if you think there is a better way of doing this.

---

