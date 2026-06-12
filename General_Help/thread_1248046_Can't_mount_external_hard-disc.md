---
title: "Can't mount external hard-disc"
date: 2009-08-23
forum: General Help
---

### Post by Nikolajd on 2009-08-23
Hey,

I just installed ubuntu and I'm having troubles with my external harddisk. When i try to open it, it says that I can't mount because the ntfs is marked to be in used. 

I would be really thankful if someone could tell me how to open it.

---

### Post by scouser73 on 2009-08-23
Follow the instructions set out in this tutorial: [[COLOR="Red"]**Mount External Hard Disk**[/COLOR]]("http://www.blog.highub.com/linux/ubuntu-mount-external-hard-disk/")

---

### Post by ASchweitzer on 2009-08-23
When you get the popup saying the disk is in use, it will give you a line of commands (it's all one command, with some spaces). Type this command as-is (including spaces but not line breaks) into a terminal. This will mount the disk and fix the issue. The other option is to mount the disk on a windows system and "safely remove" it.

Windows marks the partitions in use when it mounts them, and sometimes doesn't unmark them properly, if the power is pulled before the disk is unmounted, or things like that.

Hope that helps

---

### Post by Nikolajd on 2009-08-24
> **scouser73 said:**
> Follow the instructions set out in this tutorial: [[COLOR="Red"]**Mount External Hard Disk**[/COLOR]]("http://www.blog.highub.com/linux/ubuntu-mount-external-hard-disk/")
That doesnt work... It's still not able to mount.

---

### Post by Nikolajd on 2009-08-24
> **ASchweitzer said:**
> When you get the popup saying the disk is in use, it will give you a line of commands (it's all one command, with some spaces). Type this command as-is (including spaces but not line breaks) into a terminal. This will mount the disk and fix the issue. The other option is to mount the disk on a windows system and "safely remove" it.

Windows marks the partitions in use when it mounts them, and sometimes doesn't unmark them properly, if the power is pulled before the disk is unmounted, or things like that.

Hope that helps
The command didnt work, so I'm gonna try the windows thing.

---

