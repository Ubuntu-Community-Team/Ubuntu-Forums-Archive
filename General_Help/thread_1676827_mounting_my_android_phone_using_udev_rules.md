---
title: "mounting my android phone using udev rules"
date: 2011-01-27
forum: General Help
---

### Post by pulseplanet on 2011-01-27
Hello All,

  On my droid x, I have enabled usb mass storage and Ubuntu mounts it without problems. I wanted to auto sync files to my phone and wrote wrote these simple files

File 1: /etc/udev/rules.d/95-SyncAndroidSDCard.rules
```
KERNEL=="sdc[0-9]*", SUBSYSTEM=="block", BUS=="usb", SYSFS{serial}=="015D82401501502C",  SYMLINK=="droidx_sd", RUN+="/home/user1/bin/sync_androidphone_sdcard droidx_sd"
```

File 2: /home/user1/bin/sync_androidphone_sdcard
```
#!/bin/bash
DEVICE=$1
date > ${DEVICE}/linuxbackupdate.txt
date > /media/9B43-DE3E/linuxbackupdate.txt
date > /media/$1/linuxbackupdate.txt
```

I make sync_androidphone_sdcard executable and then rebooted the computer. Then plugged in the phone. The phone SD card is auto mounted, but I see no result (meaning no linuxbackupdate.txt file is created on the phone sd card).

Any idea what is going on? Many thanks.

KB

---

