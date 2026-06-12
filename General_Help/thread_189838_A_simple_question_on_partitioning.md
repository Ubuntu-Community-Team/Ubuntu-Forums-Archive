---
title: "A simple question on partitioning"
date: 2006-06-05
forum: General Help
---

### Post by JohanL on 2006-06-05
Well, I hope its simple.

I have Ubuntu and XP on dual boot. Works like a charm. I would, however, like to have a partition for sharing files between Ubuntu and XP. Any particular reason why I cant do that now, post-install? Theres plenty of space.

How can I do it? What tool can I use? From within Ubuntu, or from within XP?

Any help is appreciated.

Thanks

---

### Post by Kobalt on 2006-06-05
It should be really easy to do with a liveCD of your Ubuntu version and a software that's inside it : Gparted. You'll be able to resize your old partition and create your new one. Try to chose NTFS or Fat 32 for the new partition so that you can use it with both OSes : search this forum if you want to know what format is the best, I honestly have no idea on that point. 

Cheers !

---

### Post by smartalecks on 2006-06-05
Should be possible, you'll have to be careful, however, as the filesystem formats Ubuntu and XP use are different. 

Windows = NTFS or FAT32
Ubuntu = Extended 3 (EXT3)


Gparted is used from a LiveCD, either the Ubuntu LiveCD or its own (either should be fine, I'd choose the former)

Gparted Links:

[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
[http://www.linux.com/article.pl?sid=06/04/25/1917228](http://www.linux.com/article.pl?sid=06/04/25/1917228)
[http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted)

---

### Post by nanotube on 2006-06-05
there is a (free) software for windows that will let it read/write linux ext2/ext3 partitions. so the simplest would just be to install that on your windows, and then you can read anything from windows. so you don't really have to make a new partition to do this.

here is the link to that driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by anaconda on 2006-06-05
[QUOTE=nanotube]there is a (free) software for windows that will let it read/write linux ext2/ext3 partitions. so the simplest would just be to install that on your windows, and then you can read anything from windows. so you don't really have to make a new partition to do this.[/QUOTE]

Yep. that is a good idea. I have used that a lot without any problems.

NTFS  - is not good. Linux can't write to it properly
FAT32 - not good. windows has problems if size bigger than ~30GB
ext3 - perfect. Windows can read/write (if the above drivers are installed), and so can linux...

---

### Post by JohanL on 2006-06-05
Great. Exactly what I wanted to hear. I will look into this fs-driver thingy.

Thanks guys!

/Johan

---

### Post by tmastran on 2006-06-05
[QUOTE=JohanL]Well, I hope its simple.

I have Ubuntu and XP on dual boot. Works like a charm. I would, however, like to have a partition for sharing files between Ubuntu and XP. Any particular reason why I cant do that now, post-install? Theres plenty of space.

How can I do it? What tool can I use? From within Ubuntu, or from within XP?

Any help is appreciated.

Thanks[/QUOTE]

I use fat32 since writing to it from both systems is fully supported. I created a 100 gig fat32 partition using linux. I forget what tool, but gparted should work. The nice thing about doing it with linux is you are not crippled to the arbitary 32 gig limit imposed by Microsoft.

/dev/sdb1              98G   48G   51G  49% /media/fat32

---

