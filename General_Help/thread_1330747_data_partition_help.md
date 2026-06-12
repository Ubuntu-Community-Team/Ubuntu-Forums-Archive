---
title: "data partition help"
date: 2009-11-18
forum: General Help
---

### Post by texas.chef94 on 2009-11-18
SOLVED When I upgraded to 9.10 I decided to repartition as well., not taking into account the possibility of mistakenly deleting my data partition. For the experienced user this is a so what! But that partition had all my command line notes and without it I am in deep you know what in configuring another data partition. The partition is sda4 labeled data. So beyond creating the data directory I need all the command lines to get back in business.

Thanks for your help.

---

### Post by drs305 on 2009-11-18
You just want to create and use a data partition, not recover a lost partition, right?

```

sudo mkdir /mnt/data
sudo chown -R *yourusername:* /mnt/data

```

Get the UUID for the data partition (sdXX):
```
sudo blkid | grep sdXX
```

Backup fstab and open for editing, and get the partition UUID for sdXX:
```

sudo cp /etc/fstab /etc/fstab-backup
gksu gedit /etc/fstab

```

Add this line for an ext3 partition. If it is not ext3, check out the bodhi.zazen's fstab link at the end of the post, or let us know the format (for ext4, just change to match) :
> 
UUID=XXXX /mnt/data ext3 defaults,users 0 2


Mount the new partition. If you get no errors, it mounted correctly:
```

sudo mount -a

```

Even better (0r more useful) than the UUID, label it with:
```

sudo tune2fs -L data /dev/sdXX

```
Then change fstab UUID= to LABEL=data

For more help with fstab, check out this thread:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by texas.chef94 on 2009-11-18
Just what I wanted in detail. Thank you so much

Allen

---

