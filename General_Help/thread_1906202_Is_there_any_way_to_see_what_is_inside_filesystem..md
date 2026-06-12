---
title: "Is there any way to see what is inside filesystem.squashfs?"
date: 2012-01-08
forum: General Help
---

### Post by Learning Linux 2011 on 2012-01-08
Hi,

I downloaded Debian and noticed that when you browse the CD (or DVD) it lists every package alphabetically in a folder called pool, which I think is pretty cool.

Since Ubuntu is based on Debian, I thought I'd try to see how Ubuntu differed, but I noticed that Ubuntu only has something called **filesystem.squashfs** which I assume has all the packages inside of it.  

Is there a way to "open" **filesystem.squashfs** to see what is inside of it?  

I'm currently using Ubuntu 11.04

---

### Post by Buntumatic on 2012-01-08
As with any other filesystem you need to mount it, to do that you must have correct filesystem driver, in this case it is for squashfs. Not sure if installed Ubuntu has it by default, but it certainly can be added if needed. If my memory serves me correctly squashfs is read only by design, so you cannot write to it.

---

### Post by Cheesemill on 2012-01-08
If you look at a Ubuntu alternate install CD you'll find the equivilent pool directory.

The .squashfs on the live cd doesn't actually contain any .deb packages, it is a compressed root filesystem from an installed OS.

If you want too take a look you can mount it on /mnt (as an example) -
```
sudo mount /path/to/store/squash_image /mnt -t squashfs -o loop
```
You may have tou install squashfs-tools first.

---

### Post by Learning Linux 2011 on 2012-01-08
Oh, ok, I see now.  

filesystem.squashfs is a compressed, more-or-less already installed version of Ubuntu linux.

I downloaded those squashfs tools (unsquashfs) and unsquashed/expanded that file.

You are right, I think I am looking for a non-"Live" CD.

---

### Post by Cheesemill on 2012-01-08
That would be the alternate install CD found here:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

