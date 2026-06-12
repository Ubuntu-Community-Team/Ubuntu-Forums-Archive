---
title: "Can't write to a partition that was created during installation"
date: 2010-03-04
forum: General Help
---

### Post by susanne260 on 2010-03-04
Hi guys! :KS

I just finished installing Karmic Koala on my computer a little while ago... and I chose to partition the drive manually.


My computer has 2 hard drives:

Here's the HDD which boots first and has Grub and Ubuntu on it:
Screenshot: [http://i49.tinypic.com/2ahcff8.png](http://i49.tinypic.com/2ahcff8.png)

And my second HDD which has Windows and a backup partition called "datas":
Screenshot: [http://i50.tinypic.com/14yanoz.png](http://i50.tinypic.com/14yanoz.png)


And here's a copy of my /etc/fstab file:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=99ef9694-81ae-4f60-8645-3e2eda28f993 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=0973b68c-3bf3-4b74-ba6b-4324a76cddd6 /home           ext4    defaults        0       2
# /media/archives was on /dev/sdb8 during installation
UUID=b56fa1c0-7df2-4fd9-a8b0-f761eca7cbdb /media/archives ext4    defaults        0       2
# /media/datas was on /dev/sda2 during installation
UUID=bf89b1c8-93c5-4083-95ae-9823a546ef39 /media/datas    ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=3691181a-e0dd-4a5b-b5dc-59c3f3555c81 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


The ext3 partition on the 250GB drive called "datas" is an old partition that I created while I was still using Intrepid... and it works just fine.

However the partition called "archives", which I created during the installation of Karmic, doesn't seem to work properly. For some reason I can't write any files or folders on it. Why is that? :D

---

### Post by rnerwein on 2010-03-04
hi
i think may be you have a permission problem with this partition. you have may be the same user name 
but not the same USERID (number). i don't know the uid's of intrepid but in Karmic Koala they start 
with 1000.
hope that's a hint.
ciao

---

### Post by oldfred on 2010-03-04
If you run this:
sudo ls -ld /media/*

Does it show you as the owner & with permissions.

Or if you cd /media/archive and run the ls -ld does it show you as owner with permisions. Directorys may have root as owner. 

cd /media/archive
sudo chmod -R 777 /archive
sudo chown -R fred:fred /archive
where fred should be your login name

---

### Post by susanne260 on 2010-03-04
Thanks for the replies! :KS

I did a bit of googling and found out that I only needed to run the following command:

```

sudo chown -R susanne:susanne /media/archives/

```

Works like a charm now! ^^

---

