---
title: "Auto mount ext3 fs with rw access!!"
date: 2006-03-31
forum: General Help
---

### Post by Jellman01 on 2006-03-31
Hey all! 

Ive just moved over to ubuntu from xp :twisted: , and all is good so far. (apart from setting up my x800xl pci-e drivers, but all is sorted now.)

Ive got one sata drive that i would like to use as a system drive (80gb) and one 250GB sata drive that i would like to use for general storage. 

I have formatted the 250gb hdd in ext3 (i assume thats the correct file system.) Im having trouble however, once i mount it i cannot write to it, it says thet its owned by root, (ive tried sudo chmod 777 /dev/sdb1, with no luck :( ). I would also like to auto mount this drive (once the permisions are sorted out), i understand this is done with FStab.

Ive tryed messing about with it, this is what ive got so far (with no luck). 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sdb1       /media/storage  ext3    rw        0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

can any one help ?

Thanks alot in advance :-D  ](*,) 

Scott

---

### Post by Irony on 2006-03-31
To access ext3 I have defaults rather than rw, maybe it should be;

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/sdb1 /media/storage ext3 defaults 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/PHP]

---

### Post by dcstar on 2006-03-31
[QUOTE=Jellman01]
.......
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sdb1       /media/storage  ext3    rw        0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

can any one help ?

Thanks alot in advance :-D  ](*,) 

Scott[/QUOTE]
Add in "defaults" as suggested, also check that the mount point directory has the correct permissions.

---

### Post by Jellman01 on 2006-04-01
hey all, ok ive set the option to default on fstab and chmod'd the permissions on "/media/storage" (the mount point) but i still cannot wirte to the drive, create new folder etc is blanked out.

any ideas? :)

---

### Post by Irony on 2006-04-01
Do;

[PHP]sudo fdisk -l[/PHP]

To see if it is linux 83, also look at;

*System Tools > GParted*

To see whether it says linux 83.

Are you sure it is ext3 filesystem - if there is nothing on it do;

[PHP]sudo umount /media/storage
sudo mkfs.ext3 /dev/sdb1
sudo mount /media/storage[/PHP]

This will make sure it is ext3 filesystemed.

---

