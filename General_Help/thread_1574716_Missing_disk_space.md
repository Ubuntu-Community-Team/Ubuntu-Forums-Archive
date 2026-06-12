---
title: "Missing disk space"
date: 2010-09-14
forum: General Help
---

### Post by tx42 on 2010-09-14
The df shows 33GB used at /

$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     36G   33G  1.1G  97% /
none      devtmpfs    1.3G  276K  1.3G   1% /dev
none         tmpfs    1.3G  268K  1.3G   1% /dev/shm
none         tmpfs    1.3G  128K  1.3G   1% /var/run
none         tmpfs    1.3G     0  1.3G   0% /var/lock
none         tmpfs    1.3G     0  1.3G   0% /lib/init/rw
none       debugfs     36G   33G  1.1G  97% /var/lib/ureadahead/debugfs

The disk analyzer accounts for 18 GB, it is running as gksudo baobab (see picture below).

So where is the rest?

[IMG]http://i853.photobucket.com/albums/ab92/tx42/Screenshot-DiskUsageAnalyzer.png?t=1284498329[/IMG]

---

