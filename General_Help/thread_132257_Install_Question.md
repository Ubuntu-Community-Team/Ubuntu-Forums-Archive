---
title: "Install Question"
date: 2006-02-17
forum: General Help
---

### Post by jasrog on 2006-02-17
How exactly does one permanently install linux (Ubuntu) and still get the choice to use windows or Linux (Ubuntu)?

---

### Post by sevir on 2006-02-18
You can partition your H.D., or if you have two H.D.s you can set them on Cable Select by repositioning your Jumpers (this works realy well)

---

### Post by cotcot on 2006-02-18
So dual boot windows ubuntu. Somebody wrote this comprehensive howto :

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by chuckles on 2006-02-18
[QUOTE=jasrog]How exactly does one permanently install linux (Ubuntu) and still get the choice to use windows or Linux (Ubuntu)?[/QUOTE]

If you already have Windows on your computer, you can use something like Partition Magic to shrink the existing size of your windows partition (Usually the "C" drive) and create some freespace.  

What I did was this:

Allocated 30gb of 100 gb hd for Linux with partition Magic  Left it as "unformated"

Created 1.5 gb Fat32 partition as Share partition so I could pass files from one OS to another.  ( this is very helpful!!)

Used Ubuntu cd to install.  When I got to the partition section, I seleced to Manually create partitions.  I selected the "FreeSpace" that was there and asked Ubuntu to auto created the partitions it needed within that space.  Ubuntu then installed everything in that partition and installed GRUB in my master boot record (overwrote the windows one)  

When I restared computer, I could then select which OS to start.  

All told, it took about 2 hours to do.

NOTE:  For security I suggest you make a Ghost image of your HD before you attempt shrinking your drive space, and doing the install, just in case anything messes up, you can reload your image and you've lost nothing.

:)

---

### Post by aysiu on 2006-02-18
[QUOTE=cotcot]So dual boot windows ubuntu. Somebody wrote this comprehensive howto :

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)[/QUOTE] I second the motion.

---

