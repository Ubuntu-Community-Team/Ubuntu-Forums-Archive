---
title: "Tell kernel to reread partition table while one partition mounted"
date: 2010-02-05
forum: General Help
---

### Post by bakegoodz on 2010-02-05
Is there a program that will reread the partition table and update the kernel even if one of the unmodified partitions is mounted?

I installed my system on one partition, then I added another with free space. Now I want to format the second partition, but the kernel doesn't know about it yet. I tried sfdisk -R /dev/sda, but it refuses while the root partition is mounted. Is there anyway I can avoid rebooting?

---

### Post by wirelessmonkey on 2010-02-05
I believe you need to specify the partition number in your command, *NOT* the disk.

Your root partition is sdax. Where 'x' is a number. 

If you do a 
```

sudo fdisk -l 

```

You'll see a list of your partitions, and you'll be able to determine which to format. (hopefully)

---

### Post by bakegoodz on 2010-02-06
WooHoo! I found it! Just Type: partprobe

[http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html](http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html)

---

