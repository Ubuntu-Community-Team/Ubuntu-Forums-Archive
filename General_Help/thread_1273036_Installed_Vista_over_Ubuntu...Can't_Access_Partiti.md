---
title: "Installed Vista over Ubuntu...Can't Access Partition"
date: 2009-09-22
forum: General Help
---

### Post by MegaToTheMax on 2009-09-22
Please don't hate me for mentioning Vista.

I had been using Ubuntu for all of my computer activities for a while, but I installed Vista and now I can't figure out how to access Ubuntu anymore. 

I installed Neogrub, but it won't load the Linux partition.

---

### Post by lisati on 2009-09-22
Are you able to boot from a Live CD? If so, there are options for figuring out where Ubuntu has apparently disappeared to.

---

### Post by Darkwing-Duck on 2009-09-22
This happens quite a bit don't worry. I have a perfect tutorial for fixing this.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this can be of some help for ya.

---

### Post by MegaToTheMax on 2009-09-22
Thanks. Will give that a shot.

---

### Post by MegaToTheMax on 2009-09-25
> **Darkwing-Duck said:**
> This happens quite a bit don't worry. I have a perfect tutorial for fixing this.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this can be of some help for ya.

I ran through everything in the guide. Everything worked perfectly!

One snag, Windows doesn't show up in the boot menu :rolleyes:

How do I add Windows back to GRUB?

---

### Post by MegaToTheMax on 2009-09-25
Looked through my partitions. Its looks like the NTFS partition is not seen as mounted.
[IMG]http://i50.photobucket.com/albums/f350/DZimmerly/Screenshot-1.png[/IMG][IMG]http://i50.photobucket.com/albums/f350/DZimmerly/Screenshot.png[/IMG]

Really confused.....

---

### Post by sea_monkey987 on 2009-09-25
this should tell you how to do it:
[http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

except for doing the
```
root     (hd0,2)
```
line, put in the line
```
root     (hd0,1)
```

---

### Post by MegaToTheMax on 2009-09-25
Worked perfectly!

I love you.

---

