---
title: "Getting rid of Windows"
date: 2009-12-11
forum: General Help
---

### Post by Carborundum on 2009-12-11
I've been using Ubuntu (or rather, eeebuntu, to be exact) for a few months now. When I first installed it I decided to partition my SSD to keep Windows XP. However, since then I haven't used Windows at all, so I'd like to be rid of it. Ideally, I want to add it to my eeebuntu partition, but if that's not possible I'll settle for just formatting it as ext3. What's the best way to accomplish that?

---

### Post by halj32 on 2009-12-11
Just use one of the partitioning tools and format as ext 3

---

### Post by benjaminsuman on 2009-12-11
Using gparted you should be able to delete you XP partition and then resize your Ubuntu partition to include the new free space.

---

### Post by Carborundum on 2009-12-11
GParted, huh? Can I boot that from a USB flash drive? I don't have an optical drive, you see.

---

### Post by tyler756 on 2009-12-11
Do you find Ubuntu to be better than Windows?  Why?

---

### Post by RedSingularity on 2009-12-11
> **Carborundum said:**
> GParted, huh? Can I boot that from a USB flash drive? I don't have an optical drive, you see.


Yeah you can use it from a live CD/USB.

---

### Post by Carborundum on 2009-12-11
I find that it's faster, more intuitive, and a lot easier to find help for. Also, it's free.

---

### Post by Carborundum on 2009-12-11
OK, now I've run GParted. The result is... dissatisfying. The maximum capacity of my eeebuntu partition is still listed as 4.7 GB in disk usage analyzer. In GParted it says the size of the partition should be 15 GB, but somehow 13 of those are used. Also, GRUB still has the option to boot into XP. If I try to do so it says it can't, obviously, but I'd rather just be rid of it altogether.
[IMG]http://s800.photobucket.com/albums/yy287/Carborundum_pb/?action=view&current=dua_vs_gparted.jpg[/IMG][IMG]http://s800.photobucket.com/albums/yy287/Carborundum_pb/?action=view&current=dua_vs_gparted.jpg[/IMG]
[IMG]http://s800.photobucket.com/albums/yy287/Carborundum_pb/?action=view&current=dua_vs_gparted.jpg[/IMG]

---

### Post by fbugnon on 2009-12-11
> **Carborundum said:**
> The maximum capacity of my eeebuntu partition is still listed as 4.7 GB in disk usage analyzer.

I guess this has something to do with the fact you're using and extender patition for your eebuntu and that your XP partition was (I suppose) a logic one.  Maybe -- that's just a guess -- the logic partition could not be integrated into the extended.  That's why you still see 4,7 GB instead of 15 GB.


> **Carborundum said:**
>  Also, GRUB still has the option to boot into XP. If I try to do so it says it can't, obviously, but I'd rather just be rid of it altogether.
To get rid of XP option in Grub, you can either: (i) make a grub update; or (ii) manually edit the file /boot/grub/grub.cfg and delete or comment (#) the Windows XP option (be careful not to mess with other stuff or you might not be able to boot your sistem afterwards).

Hope it helps!

[[IMG]http://brainstorm.ubuntu.com/idea/22422/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22422/)

---

### Post by Carborundum on 2009-12-11
I don't have a /boot/grub/grub.cfg, but I do have a /boot/grub/menu.lst, and changing some stuff in there got rid of the XP option. About the partitions, is there anyway I could fix that?

---

### Post by joes7 on 2009-12-11
Format. You should've had installed Ubuntu on a different partition.

---

### Post by Carborundum on 2009-12-11
Oh, well. I feared that would be the ultimate solution. Unless there are other bids, I suppose I'll do that.

---

### Post by fbugnon on 2009-12-11
> **Carborundum said:**
>  About the partitions, is there anyway I could fix that?

There might be, but I'm not sure how - sorry!

Unless you have heavily customized your operational system, I would say it could be much, much easier to _reinstall the system _(fresh install).

If you don't want to do this, you might be able to do a work around, very complicated (there might be easier ways - I don't know), basically:
1. create a Linux partition in the free space left by your Windows;
2. move all the content of your present eebuntu partition into the new one (created in 1).
3. boot with a live-cd/usb and update the grub of your system (in the new partition - you might want to test to see if it works before proceeding to 4).
4. delete the old-eebuntu partition; and, finally
5. add the free space left into the partition created at 1.

As you can see, I don't think this is worth the hassle.  Additionally, this procedure is very likely to take a lot of time and might break your system.

Hope it helps (and that you choose to simply reinstall (backing up important data previously).

[[IMG]http://brainstorm.ubuntu.com/idea/22422/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/22422/)

---

### Post by Draygera on 2009-12-11
Where's your swap space at? It could be that; I ran into that problem last time I dual-booted.

[http://www.webupd8.org/2009/04/convert-your-ext3-file-system-to-ext4.html](http://www.webupd8.org/2009/04/convert-your-ext3-file-system-to-ext4.html)

This might also help you. Just make sure to backup important files.

---

### Post by joes7 on 2009-12-11
Delete your windows folder.

---

