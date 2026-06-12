---
title: "Downgrade from 64 to 32"
date: 2006-02-15
forum: General Help
---

### Post by xEN6 on 2006-02-15
I've been runing 64 bit Breezy on one of my machines at home, and it has served well.  However there's still a couple of things that don't work properly or just don't work at all under 64 bit and this is now starting to cause me some headaches...

I was wondering if there is any easy way to "downgrade" to a complete 32 bit install without formatting the partition.  (that'll teach me to install the whole drive as one partition!  d'oh!)

Thanks

---

### Post by dcstar on 2006-02-15
[QUOTE=xEN6]I've been runing 64 bit Breezy on one of my machines at home, and it has served well.  However there's still a couple of things that don't work properly or just don't work at all under 64 bit and this is now starting to cause me some headaches...

I was wondering if there is any easy way to "downgrade" to a complete 32 bit install without formatting the partition.  (that'll teach me to install the whole drive as one partition!  d'oh!)

Thanks[/QUOTE]
In theory you should be able to follow the version "Upgrade" procedure with a 32 bit Ubuntu boot disk:

[http://ubuntuforums.org/showthread.php?t=74990](http://ubuntuforums.org/showthread.php?t=74990)

---

### Post by bouncingmolar on 2008-01-05
That thread doesn't exist anymore how do you do it? :)

---

### Post by philinux on 2008-01-05
An option would be to move home to a separate partition. Follow psychocats link. Then install 32 bit but mark home for not format.

---

### Post by bouncingmolar on 2008-01-05
> **philinux said:**
> An option would be to move home to a separate partition. Follow psychocats link. Then install 32 bit but mark home for not format.

That sounds logical. 

Is there something you think I should look for on the psychocats link?

cheers.

---

### Post by aimran on 2008-01-05
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Basically, repartition your HDD so you can have a new partition for /home. Move your existing partition to the new partition. Then reinstall 32bit Ubuntu onto the old partition.

---

### Post by zvacet on 2008-01-05
Maybe this is off topic,but why don´t you install Dapper?Breezy is not supported anymore,and if you install Dapper you will be able to upgrade to 8.04 directly when it comes.Just idea nothing more.

---

