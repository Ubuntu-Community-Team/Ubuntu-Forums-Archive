---
title: "mdadming wants /dev/md/0 but /dev/md0 exists"
date: 2011-09-13
forum: General Help
---

### Post by micahgalizia on 2011-09-13
Hi,

I have been running a mdadm RAID5 reliably for about a month and now all of a sudden I'm unable to get the array working.

After the array stopped working I noticed I had a /dev/md127. Googling around I found out that the /etc/mdadm/mdadm.conf file was using the wrong UUID for the array. I'm not sure what happened to get them out of sync, I added the correct Array UUID (as per ```
sudo mdadm --examine /dev/sdb1
```, the first disk of the array).

With that fixed, when I reboot I now get the device created at /dev/md0. Googling around some more, it seems that the initramfs mdadm.conf is out of sync with my mdadm.conf. There are steps to fix the problem [here]("http://ubuntuforums.org/showthread.php?t=1764861") but the aren't quite working for me. When I run ```
update-initramfs -u
``` I get this:

```
mdadm: cannot open /dev/md/0: no such file or directory
```

For some reason mdadm is expecting /dev/md/0 to exist and seems to be ignoring /dev/md0. If I run ```
sudo mdadm --examine --scan
``` I get:

ARRAY /dev/md/0 ....

Again, a device that doesn't exist.

Does anyone have any suggestions?

---

