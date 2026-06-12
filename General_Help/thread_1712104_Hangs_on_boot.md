---
title: "Hangs on boot"
date: 2011-03-22
forum: General Help
---

### Post by the_jlx on 2011-03-22
i have to use ctrl+alt+F2 login and sudo start gdm to get into ubuntu.
link to image below.
Grabs a beer and awaits some smarty to give me a idea how to fix it.:popcorn:
[http://jlxsolutions.com/IMG_0002.JPG]("http://jlxsolutions.com/IMG_0002.JPG")
i think it is probably waayyy to big to insert.

---

### Post by TeoBigusGeekus on 2011-03-22
A reinstallation of gdm perhaps?
```
sudo apt-get install --reinstall gdm
```

---

### Post by the_jlx on 2011-03-22
Well even i realise this is not a gdm issue :)
hardrive something something
Sigh...
Will attempt to write off that pic instead of having pic link:

ata5.00 failed command: SET FEATURES
ata5.00 cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 0
        res 40/00:00:00:00:00/00:00:00:00:00/40 emask 0X4 (timeout)

ata5.00: status { DRDY }
sd 4:0:0:0:0: timing out command, waited 7 s

---

### Post by the_jlx on 2011-03-22
EDIT: (Hmm swinedows drive dying? but what has that to do with linux when  it works fine under swinedows)

hmm this came out of nowhere suddenly O_o
maybe related:
Error mounting: mount exited with exit code 13: Error reading bootsector: Input/output error
Failed to sync device /dev/sdb1: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

