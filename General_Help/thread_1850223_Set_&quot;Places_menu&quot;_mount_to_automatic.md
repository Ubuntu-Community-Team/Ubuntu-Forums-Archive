---
title: "Set &quot;Places menu&quot; mount to automatic?"
date: 2011-09-26
forum: General Help
---

### Post by kevinmd88 on 2011-09-26
I'm a complete newbie to Ubuntu. Is there is a way to automate the mounting of a partition as if I had clicked it in the Places menu at the top? I have an NTFS data partition, and as it stands right now I have to click Places > Data every time I log on... I'm wondering if there is a way to mount this partition on startup as if I had clicked it; whatever commands this menu executes is exactly what I want to automate.

Hopefully I explained this correctly. Thanks in advance for helping.

---

### Post by garvinrick4 on 2011-09-26
Open a terminal and run this and add line as per below and save.
```
gksudo gedit /etc/fstab
```Add your NTFS partition to fstab and save and reboot.
I will show you my partition to go by. Use your own UUID and partition sda#.
```
sudo blkid
``` (lower case L) to get UUID of that partition.

Mount point of /media/data  is the same just change what in red to yours.
# /dev/[COLOR=Red]sda8[/COLOR]
UUID=[COLOR=Red]1927A02F2C3A884A[/COLOR] /media/data  ntfs-3g defaults,local=en_US.utf8 0 0

Link to bookmark and study when time permits below.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by kevinmd88 on 2011-09-26
Thank you. This worked like a charm.

---

