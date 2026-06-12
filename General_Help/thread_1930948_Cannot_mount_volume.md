---
title: "Cannot mount volume"
date: 2012-02-24
forum: General Help
---

### Post by MikeLIT on 2012-02-24
Playing middle man between two different users that don't know much about ubuntu or Linux. One party backed up an old website to USB drive and shipped to another party to get data off of the drive. The problem is that they receive the following error when trying to mount the USB drive:
 
*Cannot mount volume.*
*Unable to mount the volume 'usb backup'.*
*Details*
*mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail or so*
 
Had them enter the terminal and enter the following command:
 
*sudo fdisk -l *
 
Output is below. Any ideas on what I can have them try to mount this drive without losing data? We just need to get data off this drive. Thanks in advance for any help.
 
[IMG]http://dl.dropbox.com/u/20880671/Output.png[/IMG]

---

### Post by roelforg on 2012-02-24
Try to mount again and then give us the output of
```

sudo dmesg | tail

```

---

