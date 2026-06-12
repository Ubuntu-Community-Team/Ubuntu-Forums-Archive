---
title: "Partition table disappeared..."
date: 2006-06-28
forum: General Help
---

### Post by atomicSpatule on 2006-06-28
I installed windows XP after ubuntu dapper, and I reinstalled grub. But now my partition table disappeared, in gparted my whole hard drive shows as unpartitionned space. However, I can still mount partitions... Can anybody help me? I really can't just format and start over...

---

### Post by amohanty on 2006-06-29
Can you boot up and use both OS's?

AM

---

### Post by richbarna on 2006-06-29
[QUOTE=atomicSpatule]I installed windows XP after ubuntu dapper, and I reinstalled grub. But now my partition table disappeared, in gparted my whole hard drive shows as unpartitionned space. However, I can still mount partitions... Can anybody help me? I really can't just format and start over...[/QUOTE]

I've got the same problem after a dual Dapper install, If I find any thing i'll post back.
Everything boots and works fine, but I think gparted made a mistake and added an extra partition that I would like to remove.

My other post :-
[http://www.ubuntuforums.org/showthread.php?t=205585]("http://www.ubuntuforums.org/showthread.php?t=205585")

And someone elses post :-
[http://www.ubuntuforums.org/showthread.php?t=204546&highlight=gparted]("http://www.ubuntuforums.org/showthread.php?t=204546&highlight=gparted")

---

### Post by aysiu on 2006-06-29
[This](http://geekblog.oneandoneis2.org/index.php?title=triumph_aamp_tragedy&more=1&c=1&tb=1&pb=1) may help.

---

### Post by richbarna on 2006-06-29
I did > $ sudo fdisk /dev/hdc 

and clicked m for help, and then l to list the partitions, and found that I had two extra partitions.
Whatsmore, I checked disk manager and found that gparted had actually created my new Dapper partition as swap instead of home.
So I deleted the new installation and then had a grub problem and couldn't boot, so I put in my Dapper cd and hey presto gparted works again.
I am now going for a reinstall on the empty partition.

So basically, I think you need to first do $ sudo fdisk /dev/hard disk name *mine is hdc*,
press l to list your partitions and then delete any extra partitions for gparted to work.

But be careful and have your cd handy in case there is a grub problem at boot.

EDIT: Fixed.

I repartitioned and did a new install and now everything works, including gparted.

---

