---
title: "Automount pendrive not working (12.04)"
date: 2012-09-29
forum: General Help
---

### Post by Iceberg76 on 2012-09-29
dmesg | tail
> [68233.038041] sd 19:0:0:0: [sdc] No Caching mode page present
[68233.038051] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[68233.039184]  sdc:
[68233.043399] sd 19:0:0:0: [sdc] No Caching mode page present
[68233.043409] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[68233.043418] sd 19:0:0:0: [sdc] Attached SCSI removable disk


Pendrive can be mounted with:
sudo mount /dev/sdc /media/pendrive

I set dconf-editor org/desktop/media-handling automount to 'yes'.

Problem started when I used once the pendrive under Windows 7.

---

### Post by juliohm on 2012-11-05
I'm having the same issue. External USB drives and flashdrives are not mounting automatically at /media/*

I have to manually mount USB drives to whatever location to access them. As far as I can tell, I can't see any significant error messages in /var/log/syslog about this.

A solution will be appreciated.

---

### Post by juliohm on 2012-11-05
Quick update.

I am able to mount USB drives using

```
gvfs-mount -d /dev/sdNN
```

For example

```
gvfs-mount -d /dev/sdc1
```

This will mount the drive to /media/{DEVICENAME} just like we are used to in the GUI.

I just don't understand why this mount is not being done automatically.

---

