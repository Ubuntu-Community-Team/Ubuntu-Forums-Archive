---
title: "How to mount partition on startup?"
date: 2010-06-22
forum: General Help
---

### Post by chroncile on 2010-06-22
I am running Ubuntu 10.04 and I have a partition which contains my Windows files. I have made shortcuts to some of the programs and placed them on my desktop, however, every time I restart Ubuntu, the shortcuts become broken until I mount the partitions.

How do I make it so Ubuntu automatically mounts the partitions on startup?

---

### Post by dabl on 2010-06-22
You must edit /etc/fstab to add a mount line for each additional partition that you want to mount at boot time:

[http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by r_s on 2010-06-22
You can install NTFS configuration Tool using synaptic...it's easier to use and modifies the fstab automatically.

---

### Post by stinkeye on 2010-06-22
.....or you could install **ntfs-config** through synaptic for a simple GUI 
to mount windows partitions at boot.
Oh woe,
I'm too slow.[COLOR="Gray"][/COLOR]

---

