---
title: "How to view and print your disk partition table in ubuntu 11"
date: 2012-02-24
forum: General Help
---

### Post by nathanh13 on 2012-02-24
Hi,
I was wondering how to find my disk partitions table in ubuntu.

Thanks in advance for any help.

Yours,

Nathan

---

### Post by HeroOfCanton on 2012-02-24
```
sudo fdisk -l
```

(That's L not one)

---

### Post by oldfred on 2012-02-24
Welcome to the forums.

You can list partitions several ways with somewhat different information:

sudo fdisk -lu
sudo parted /dev/sda unit s print
sudo sfdisk -d /dev/sda
To see UUIDs
sudo blkid

or create a file from sfdisk to have a backup of table:

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

You can copy any of the terminal outputs to a text file with copy & paste if you want.

---

### Post by ohadcn on 2012-02-24
have you tried gparted?

---

