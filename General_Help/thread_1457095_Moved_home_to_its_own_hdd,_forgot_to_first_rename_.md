---
title: "Moved /home to its own hdd, forgot to first rename old to /home.old"
date: 2010-04-18
forum: General Help
---

### Post by Kurtosis on 2010-04-18
Hi all, I just moved /home to a second hard drive using [the guide at IBM's site]("http://www.ibm.com/developerworks/library/l-partplan.html").

However, I forgot to first rename the old /home to /home.old, and now that I've remounted the second hard drive to /home, I don't know where the files in the old /home are.

When I installed ubuntu I used the default partition options.  Is the old /home hidden on /dev/sda3 or sda5 or someting?

Also, is there a command that shows what partition any directory in the filesystem is mounted to?  I'd just like to verify that the new /home has /dev/sdb1 mounted to it.

Thanks!

---

### Post by iponeverything on 2010-04-18
Just do:

```

cd /
sudo umount /home

```

And your old home will show up. It's a bit of an old-school way of hiding directories..

---

### Post by john newbuntu on 2010-04-18
run:
df -Th
and verify the location of new home by looking at the first and last columns.

---

### Post by Kurtosis on 2010-04-18
> **iponeverything said:**
> Just do:

```

cd /
sudo umount /home

```

And your old home will show up. It's a bit of an old-school way of hiding directories..
Thanks, just did it.  Why does this work, is the default home partition hard coded somewhere as a backup?

---

### Post by Kurtosis on 2010-04-18
> **john newbuntu said:**
> run:
df -Th
and verify the location of new home by looking at the first and last columns.
Thanks!

---

### Post by iponeverything on 2010-04-18
> **Kurtosis said:**
> Thanks, just did it.  Why does this work, is the default home partition hard coded somewhere as a backup?

In the world of file systems, things can be a bit quirky. The data didn't actually go anywhere, you just lost your ability access it. It's like having hidden passage behind a bookshelf. By design, a mount point must be a directory but it does not have to be empty -- So by mounting over a non-empty directory you just moved a bookcase in front of the hole in the wall.

---

### Post by Kurtosis on 2010-04-19
I see, you wouldn't happen to know of a good source to read up on the details of how that works, would you?

---

### Post by iponeverything on 2010-04-19
Its for Ext2 but you have to start here, before you can really understand ext3. 

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)

---

