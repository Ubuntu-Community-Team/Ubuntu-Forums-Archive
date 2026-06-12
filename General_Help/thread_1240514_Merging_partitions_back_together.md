---
title: "Merging partitions back together?"
date: 2009-08-14
forum: General Help
---

### Post by jeb800e on 2009-08-14
Is it possible for me to merge HDD partitions back together in Ubuntu? If so, how? I really need to know this! Thanks!

~Jeb800e

---

### Post by jeb800e on 2009-08-14
bump.....

---

### Post by michy99 on 2009-08-14
The only way I know is to delete one partition and expand the other to use the space. The partitions have to be next to each other, and you have to copy anything on the partition you are going to delete to another partition first.

Of course you really should backup everything first.

---

### Post by jeb800e on 2009-08-14
Do I HAVE to copy? What happens if I don't?

---

### Post by running_rabbit07 on 2009-08-14
> **jeb800e said:**
> Is it possible for me to merge HDD partitions back together in Ubuntu? If so, how? I really need to know this! Thanks!

~Jeb800e
If you don't you lose your files.

You should only bump your thread once every 24 hours, as everyone else would like to have help, too.

---

### Post by michy99 on 2009-08-14
If you don't copy the files on the partition you are going to delete, they will be gone when you delete the partition. Of course, if there is nothing on that partition you want to keep, it is not a problem.

---

### Post by jeb800e on 2009-08-14
[I]You should only bump your thread once every 24 hours, as everyone else would like to have help, too.

[/I]That taken. Sorry 'bout that! 
On my LiveCD, each time I try to use GParted, it always just stays at the loading screen, not identifying anything, yet, when I use the installer, it usually finds everything fine and quick.
I don't see a partition with /home. I DO see a partition with a /dev/sda1 , though. The others are /dev/sda4 and /dev/sda2 . The HDD's name is "/dev/sda"

---

### Post by michy99 on 2009-08-14
Just so I have a clear idea of what you are trying to do, do you have a separate /home partition and you want to move it to the main partition and have one partition using the space of the two partitions you have now?

---

### Post by jeb800e on 2009-08-14
I want to merge everything into one large partition. I do not mind if I have to reinstall Ubuntu for that.

---

### Post by michy99 on 2009-08-14
Reinstalling is one way to go. If you haven't made a lot of changes to your system that will take a long time to re-do, it might be the easiest way. Just make sure you have a copy of any data that you want to keep.

Can I ask why you want one partition? (Just curious.)

---

### Post by jeb800e on 2009-08-14
I formatted the other two partitions, as I did not use that OS anymore, as I have switched to Ubunu.

So, exactly, how do I get my HDD back together in one big partition, specifically? If I install Ubuntu, and select all partitions and select "format" on all of them, will it automatically merge them, is what you are trying to say?

---

### Post by michy99 on 2009-08-14
One of the options when you install is to use the entire disk. This will erase everything on the disk and make one big partition, except for a small swap partition.

---

### Post by jeb800e on 2009-08-14
lol, I completely forgot about that feature!
So, does it remove EVERYTHING, or does the installer leave a few files behind?

---

