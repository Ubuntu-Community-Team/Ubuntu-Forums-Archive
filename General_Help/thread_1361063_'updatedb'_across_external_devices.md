---
title: "'updatedb' across external devices"
date: 2009-12-21
forum: General Help
---

### Post by Silvernail on 2009-12-21
I have an external USB hard drive attached to this computer with data from another computer I managed to save before a hard drive failure.

I would like to use 'updatedb' and 'locate' to find stuff on that drive.

Reading the manual, it says that this environmental variable:
> PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
controls what/which areas/devices are searched.

I understand the pitfalls of scanning removable devices and then running 'locate' and the device is not there.

The manual does not tell me what to change to be able to read a removable device.

Help would be appreciated.
Thanks
Dave

---

### Post by hugmenot on 2009-12-21
You got the wrong idea about the PATH variable. That specifies in which directories programs are searched for when you start them, e.g., firefox &#8594; /usr/bin/firefox.

What you want is to edit /etc/updatedb.conf

For instructions read man "updatedb.conf"

I think you want to remove "/media" from PRUNEPATHS so that it also recurses to mounts under that path.

---

### Post by Silvernail on 2009-12-22
Worked great. Thanks very much
Dave

---

