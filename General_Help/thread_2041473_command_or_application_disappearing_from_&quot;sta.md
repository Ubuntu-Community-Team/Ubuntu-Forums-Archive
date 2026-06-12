---
title: "command or application disappearing from &quot;startup applications&quot; list"
date: 2012-08-12
forum: General Help
---

### Post by rvboutin on 2012-08-12
Hi,
I have a fresh install of Ubuntu 12.04LTS, and although the problem does not seem new, it appears as it is still unresolved...
I want to mount 2 NTFS partitions at boot-up, so I add the line ```
/usr/bin/udisks --mount /dev/*sd_name-of-my-partition*
``` for each partition, and the start-up list only keep the last one added whatever I do!!
Any help welcome!!
Cheers,
Rv

---

### Post by vexorian on 2012-08-12
this might be cause each entry uses the same program, so the applet "simplifies" things by thinking that you intend to replace a previous startup entry..

Instead, make a script

```

#!/bin/sh
/usr/bin/udisks --mount /dev/sd_name-of-your-partition
/usr/bin/udisks --mount /dev/sd_name-of-your-other-partition
/usr/bin/udisks --mount /dev/sd_name-of-your-other-other-partition

```
(etc)

Save the script fixpartitions.sh somewhere, mark it as executable in the file permissions dialog then make the startup apps call your fixpartitions.sh (full path, like /home/yourname/scripts/fixpartitions.sh

---

### Post by rvboutin on 2012-08-13
Hi,
OK thanks, will try this and post back!!
Cheers,
Rv

---

### Post by rvboutin on 2012-09-11
Hi,
Works great!! Thanks for the advice!!
Rv

---

### Post by tienlbhoc on 2012-09-11
you can use pysdm to easy use with GUI

---

