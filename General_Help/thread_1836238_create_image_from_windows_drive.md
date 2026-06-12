---
title: "create image from windows drive"
date: 2011-08-30
forum: General Help
---

### Post by loolooyyyy on 2011-08-30
is it possible to do it inside Ubuntu? not stand alone and usually expensive softwares like Norton ghost
 sure it must be recoverable after o totally formatted HDD and deleted all partitions

by the way: i know about dd,partimage and.... my question is will the windows installation be usable after recovering? recovering AFTER re-partitioning

---

### Post by YesWeCan on 2011-08-30
I'm not sure about Clonezilla (because I don't know much about it) but dd will do what you want. You'd have to copy the whole disk, tho, to make sure it will boot properly.

sudo dd if=/dev/sdx bs=64k conv=notrunc,noerror > clone.img

To restore
sudo dd if=clone.img bs=64k conv=notrunc,noerror of=/dev/sdy

see: [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by timlev on 2011-08-30
I have had good luck with Clonezilla. You can do device to device, device to image, or image to device. It combines several tools to efficiently deal with free space in NTFS (Windows) filesystems. I just use a livecd, but I think you somehow install it as a server if you have a lot of imaging to do.

---

### Post by loolooyyyy on 2011-08-30
the partition is usually 400GB so i'll try my luck with clonezilla
thank you all

---

### Post by Mark Phelps on 2011-08-31
If you just want to image your Windows install, you can download the FREE version of Macrium Reflect.  It does the same stuff Ghost did -- it just doesn't cost anything.

---

### Post by loolooyyyy on 2011-08-31
> **Mark Phelps said:**
> If you just want to image your Windows install, you can download the FREE version of Macrium Reflect.  It does the same stuff Ghost did -- it just doesn't cost anything.

perfect! thank you

---

### Post by seawolf167 on 2011-08-31
I know you have this marked as solved but I just wanted to add a big +1 for Clonezilla. I use it personally and at work and it works beautifully with Windows, *nix, etc.

---

### Post by loolooyyyy on 2011-08-31
> **seawolf167 said:**
> I know you have this marked as solved but I just wanted to add a big +1 for Clonezilla. I use it personally and at work and it works beautifully with Windows, *nix, etc.

clonezilla got stuck at calculating bitmap, am i doing anything wrong?

---

### Post by seawolf167 on 2011-08-31
Try with the older i686 version, I think this is a verified problem with the new version (AMD64 in particular)

---

### Post by loolooyyyy on 2011-08-31
> **seawolf167 said:**
> Try with the older i686 version, I think this is a verified problem with the new version (AMD64 in particular)
can you specify the version? i'm running out of bandwidth here  :(

---

