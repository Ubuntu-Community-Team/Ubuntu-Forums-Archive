---
title: "Need something like dd but more space efficient"
date: 2011-09-22
forum: General Help
---

### Post by veggen on 2011-09-22
I'm thinking about upgrading my 10.10 to 11.04, but since upgrade in general can go awry, plus I'm very skeptical about Unity, I'd like to create an image of my entire Ubuntu partition, so that I can safely go back without losing anything.

I reckon I could achieve this with dd, and I think I know how I'd go about it (boot from Live CD, dd the correct partition, and later do the reverse), but is there a tool more suited for this task? Something more efficient and space conserving than dd? Clonezilla?

Or maybe a completely different approach?

---

### Post by patryk77 on 2011-09-22
Personally, I would use dd, and yes you can use if=/dev/sda5 to read a single partition.

Some people might suggest[Clonezilla](http://clonezilla.org/), but I never used that.

As for more space efficient, you can compress the image after cloning, but it will take a long time.

---

### Post by veggen on 2011-09-22
Yup, that did sound like the most straightforward way to me too. Thanks!

---

### Post by Nostalos on 2011-09-22
or pass it through compression before writing to disk.

dd if=/device/path | gzip > filename.gz

---

### Post by YesWeCan on 2011-09-22
If you are copying a single partition, as opposed to a drive, you don't need to use dd or clonezilla. You can just copy the partition contents to a new partition, using live CD/USB:

```
sudo mkdir /mnt/oldptn /mnt/newptn
sudo mount /dev/sdwx /mnt/oldptn
sudo mount /dev/sdyz /mnt/newptn
sudo rsync -ax --progress /mnt/oldptn/ /mnt/newptn/

```
This is efficient in that the new partition only needs to be big enough to contain the contents of the old partition.

---

### Post by dcstar on 2011-09-23
> **veggen said:**
> I'm thinking about upgrading my 10.10 to 11.04, but since upgrade in general can go awry, plus I'm very skeptical about Unity, **I'd like to create an image of my entire Ubuntu partition**, so that I can safely go back without losing anything.
.........

Or maybe a completely different approach?

Simply use **gparted** to copy the partition. Change the UUID of the backup copy when the copy is finished if it is to remain on a device that is connected at boot time.

---

### Post by aysiu on 2011-09-23
I have used CloneZilla, and I would highly recommend it.

If you have a 250 GB hard drive and you *dd* it, it will copy the entire 250 GB hard drive and even if you compress it, it'll take up a lot of space (something close to 250 GB).

If, however, you have a 250 GB hard drive and use only 50 GB of it, CloneZilla's resulting image will be roughly 50 GB, and the imaging process will be a lot shorter.

---

### Post by nmaster on 2011-09-23
fsarchiver is also a very good tool.  i like to use it to back up my root partition periodically.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by Slim Odds on 2011-09-23
> **nmaster said:**
> fsarchiver is also a very good tool.  i like to use it to back up my root partition periodically.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

This part bothers me a little:>  It's still under heavy development so it must not be used on critical data. 

---

### Post by veggen on 2011-09-23
Hehe, lots of different advices :) But now I know my choices better. Thanks everyone!

---

