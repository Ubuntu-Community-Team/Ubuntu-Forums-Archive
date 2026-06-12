---
title: "how to mount a partition image using a live cd?"
date: 2010-12-13
forum: General Help
---

### Post by Seepgood on 2010-12-13
I have made an image of an old debian partition using dd to use as backup. I'm using the live cd for ubuntu 10.4 and I wanted to mount it to see if everything was copied ok. How do I do that? I tried

```
mount debian.img /tmp/mnt

```but it complained that the mount point did not exist. So I made a directory named /mnt in /tmp and tried again using -o this time as it also complained it was not a block device. Then it complained that it could not find /mnt in /etc/fstab or /etc/mtab. What do I do now?

---

### Post by Slim Odds on 2010-12-13
Try this: [http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux](http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux)

I used google with this for the search phrase: mount partition image linux

---

### Post by Seepgood on 2010-12-13
Sorry mate, the site you posted doesn't answer my question. Thanks for the effort.

---

### Post by tredegar on 2010-12-13
Try 
```
sudo -i
mkdir /mnt/olddeb
chmod 777 /mnt/olddeb
mount -o loop OldDeb.iso /mnt/olddeb
ls /mnt/olddeb
exit
```

---

### Post by Seepgood on 2010-12-13
Thanks, that worked perfectly.

---

