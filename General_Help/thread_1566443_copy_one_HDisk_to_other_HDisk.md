---
title: "copy one HDisk to other HDisk"
date: 2010-09-02
forum: General Help
---

### Post by wdbnv on 2010-09-02
Is it possible to 'copy' the complete (old and small) 80 GB HDisk to (new and bigger) 320 GB HDisk ...? and then
 
... start ubuntu 9.10 with the new 320 GB HDisk?

---

### Post by MegaLoler on 2010-09-02
If you have a mac, you can use carbon copy cloner

[http://www.bombich.com/](http://www.bombich.com/)

---

### Post by SlugSlug on 2010-09-02
yes I use dd at work to do a similar task

find out your current /dev/sd  most likely sda -- to find it 

df -h  
will show
/dev/sdb6             9.8G  4.3G  5.0G  47% /


the / is the root thats what we want.

so in my case if I wanted to clone to sdb  the command is

sudo dd=if/dev/sda of=/dev/sdb

THIS WILL WIPE SDB !!

once done either change your bios boot device or physically swap the disks round (SATA cables)

dd command will take a long time

there is also clonezilla -- i've never used it tho

---

### Post by viralmeme on 2010-09-02
> **wdbnv said:**
> Is it possible to 'copy' the complete (old and small) 80 GB HDisk to (new and bigger) 320 GB HDisk ...? and then ... start ubuntu 9.10 with the new 320 GB HDisk?

Use [Gparted]("http://gparted.sourceforge.net/screenshots.php") or [DD]("http://en.wikipedia.org/wiki/Dd_(Unix)"), then resize the new partition using Gparted..

---

