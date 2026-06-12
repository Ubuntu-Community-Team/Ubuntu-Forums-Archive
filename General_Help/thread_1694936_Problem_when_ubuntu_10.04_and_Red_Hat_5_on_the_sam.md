---
title: "Problem when ubuntu 10.04 and Red Hat 5 on the same system"
date: 2011-02-25
forum: General Help
---

### Post by anuarang on 2011-02-25
i have problem about ubuntu 10.04 i have installed ubuntu 10.04 in my lapi in different partitions.
but after installing Red Hat 5 in again different partitions, system is not asking about ubuntu to start...
as i reboot system, it ask only about 'red hat 5 and other....'
after selecting 'other...' it used to start windows 7
all the partitions of ubuntu 10.04 are available on hard disk...
so how can i start ubuntu 10.04???????

---

### Post by ajgreeny on 2011-02-25
I guess that Red Hat has taken over the grub from ubuntu with whatever RH uses.  If Red Hat uses grub2 you should be able to run update-grub as root in terminal of RH and ubuntu should appear in the menu, but as I have no knowledge of RH it may be easier to restore grub from ubuntu to the MBR of the boot disk again.

See section 13 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for details.

---

