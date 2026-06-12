---
title: "conky -"
date: 2011-11-23
forum: General Help
---

### Post by lafcina on 2011-11-23
Hi,

I'u using conky for monitoring, and have a problem with configuring (usb external) disk usage monitor.

My idea is to show disk information, but only when disk is connected, like it is shown in this part of .conkyrc configuration file:
[COLOR="Blue"]${if_existing /dev/sdb}
${if_existing /dev/sdb1}sdb1: ${fs_used_perc /media/d1}${endif}
${if_existing /dev/sdb2}sdb2: ${fs_used_perc /media/d2}${endif}
${endif}
[/COLOR]

Problem is when other disk (with different label) is connected, this configuration won't work, because it will be mounted on diferent mount point ie. [COLOR="Blue"]/mount/MyDisk3[/COLOR]. I would like universal solution which will work for any disk mounted.

Most elegant would be if man could use device name ([COLOR="Blue"]/dev/sdb1[/COLOR]) instead of mount point name ([COLOR="Blue"]/media/d1[/COLOR]) as an argument, but this is not working.


Any idea how to dynamically find and use mount point for external disks ?


P.S. It is the same with other file system varables (fs_free, fs_free_perc, fs_size, fs_type, fs_used, fs_used_perc).

---

### Post by Quackers on 2011-11-23
I think you may get more help with your problem if you post the request in this thread
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by Habitual on 2011-11-23
try this:

```
${if_mounted /dev/sdb}
${if_mounted /dev/sdb1}sdb1: ${fs_used_perc /media/d1}${endif}
${if_mounted /dev/sdb2}sdb2: ${fs_used_perc /media/d2}${endif}
${endif}
```

should be ok near conky1.8'ish...

HTH

---

