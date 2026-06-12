---
title: "Replace 10.04 On SDA1 With 10.04. How?"
date: 2010-08-20
forum: General Help
---

### Post by Mark76 on 2010-08-20
Usually if I want to do a fresh install I just wipe the disk, but this time I really want to keep my home partition and overcome a libwnck bug that can only be beaten with a fresh installation.

So I need to completely replace 10.04 on partition 1 (root) and link it to partition 2 (home). How do I do this?

---

### Post by nothingspecial on 2010-08-20
Install as normal.

When you get to the partitioning bit choose manual advanced or whatever it`s called.

Select your / partition and choose to format it and use it as an ext4 journaling file system. Give it a mount point of /

Select your /home partition and choose to use it as whatever file system it is. Give it a mount point of /home

[SIZE=4]but[/SIZE]

[SIZE=5][COLOR=Red]Do not check (tick) the format box[/COLOR][/SIZE]

and back everything up first just incase something goes wrong.

---

### Post by Mark76 on 2010-08-20
Yay. It worked :D

Thanks :)

---

### Post by madmax.santana on 2010-08-20
I did the same while I had Jaunty. It messed up, overwriting all configuration files and giving some parsing errors on boot.

---

