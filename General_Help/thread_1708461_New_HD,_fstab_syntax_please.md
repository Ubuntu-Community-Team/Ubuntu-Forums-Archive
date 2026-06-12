---
title: "New HD, fstab syntax please"
date: 2011-03-16
forum: General Help
---

### Post by stephanelefou on 2011-03-16
Hi,

I just installed, partitioned and formatted a new 500GB hard drive (EXT3) on my system (10.10)

What is the syntax I have to put in fstab in order to have the whole partition RW?  It is currently read only.

Drive name is sdb1, mounted as /500GB.

Thanks.

---

### Post by WorMzy on 2011-03-16
It probably already is, unless you explicitly told it to mount as ro. What's the output of "mount"?

Have you tried chowning the partition's root directory?

```
sudo chown -R $USER:$USER /500GB
```

(Be careful with that command. _Don't_ chown your root partition's root directory (/) by mistake.)

To answer your question, an fstab entry for that partition would look something like this:

```
/dev/sdb1 /500GB    ext3   defaults                        0 2
```

---

### Post by stephanelefou on 2011-03-16
Thanks!  It now works.  

> **WorMzy said:**
> It probably already is, unless you explicitly told it to mount as ro. What's the output of "mount"?

Have you tried chowning the partition's root directory?

```
sudo chown -R $USER:$USER /500GB
```

(Be careful with that command. _Don't_ chown your root partition's root directory (/) by mistake.)

To answer your question, an fstab entry for that partition would look something like this:

```
/dev/sdb1 /500GB    ext3   defaults                        0 2
```

---

