---
title: "Can't make iso"
date: 2010-06-02
forum: General Help
---

### Post by sisyphus1978 on 2010-06-02
I have been backing up my computers with my clonezilla pxe server. I have folders thus:

> 
[EMAIL="bob@desktop:/media/partimag/aspireonelucid.img"]bob@desktop:/media/partimag/aspireonelucid.img[/EMAIL]$ dir
Info-dmi.txt       sda2.ext4-ptcl-img.gz.aa   sda-mbr
Info-lshw.txt       sda2.ext4-ptcl-img.gz.ab   sda-pt.parted
Info-packages.txt  sda-chs.sf              sda-pt.sf
parts           sda-hidden-data-after-mbr
Trying to create an iso out of the folder doesn't work:
> 
genisoimage: Permission denied. File /media/partimag/aspireonewin7.img/sda1.ntfs-ptcl-img.gz.ac is not readable - ignoring
Any ideas?

I use clonezilla to backup my home computers. It copies the partition  and splits the files into 2000mb chunks. I then mount the /home/partimag  (where the images are stored) through nfs onto my desktop. I want to  make an iso out of the individual folders that I have for each machine.

---

### Post by sisyphus1978 on 2010-06-02
Just tried locally (on the clonezilla server) and > sudo genisoimage -o my_image.iso /home/partimag/aspireonewin7.img  did work.

But trying to burn the dvd on my desktop doesn't work.

> wodim: Permission denied. Cannot open '/media/TV/aspirewin7.iso'

---

