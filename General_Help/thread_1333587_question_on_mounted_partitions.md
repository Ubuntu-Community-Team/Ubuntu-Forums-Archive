---
title: "question on mounted partitions"
date: 2009-11-21
forum: General Help
---

### Post by underworld288 on 2009-11-21
I have noticed that in karmic partitions that are mounted in places other than /media are showed on the desktop too. I was wounder if i could change it back only to show partitions mounted in /media. For example I have mounted a partition to take the place of /home/username/Documents and it shows up on the desktop. I don't want this. 

I am aware that you can us gconf-editor to not show mounted partitions on the desktop but I still want partitions mount in /media to be shown on the desktop. Can someone help?

---

### Post by ajgreeny on 2009-11-21
I find this surprising.  I have mounted my complete 9.04 install partition to /mnt in karmic and it does not show on the desktop, but is available for the linked documents and other personal files, allowing me to avoid duplication.  I keep all other /home configuration files separate to avoid potential problems.

How do you mount the partitions, and to what mountpoint?

---

### Post by underworld288 on 2009-11-21
i have the partition mount at boot through fstab and is mounted to /home/user/Documents. here is the line in my fstab...

> /dev/sda6       /home/user/Documents   ext3   user,exec,sync,auto   0      3


i just realized that another ubuntu box that i have has karmic on it and the partitions mount at /mnt/extra1 and /mnt/extra2 do not show up on the desktop. although the live cd's setup program setup those mounted partitions.

---

### Post by ajgreeny on 2009-11-22
So it sounds as if it is worth changing the mount point to /mnt, and perhaps the desktop icon will not show.

---

### Post by underworld288 on 2009-11-24
so maybe anything other than /mnt will show up on the Desktop? ok thanks for the help

---

