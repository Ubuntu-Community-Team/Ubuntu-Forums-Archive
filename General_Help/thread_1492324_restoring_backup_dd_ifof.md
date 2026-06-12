---
title: "restoring backup dd if/of"
date: 2010-05-24
forum: General Help
---

### Post by ZenMasta on 2010-05-24
Several months back I backed up a windows hard drive using an ubuntu live cd and this command
dd if=/dev/hdx | gzip > /path/to/image.gz

I now want to restore that image but so far have not been successful
I have tried to restore using this command
sudo dd if=/path/to/file.gz of=/dev/sdb1

After some time has passed, the terminal reads
23568129+1 records in
23568129+1 records out
12066882348 bytes (12 GB) copied, 1327.65 s, 9.1 MB/s

If I reboot to windows with the 2nd hard drive connected as a slave. I go to my computer to try and browse the files of the restored HD but when I double click the drive, windows says
the disk is not formatted.


I have also tried 
sudo dd if=/path/to/file.gz of=/dev/sdb

And when I do this, the disk does not show up in places/my computer but it will show up in gparted and Disk Management

What am I doing wrong?

---

### Post by Ocxic on 2010-05-24
"dd if=/dev/hdx | gzip > /path/to/image.gz"

You sent the data through gzip when you backed it up, all the data is compressed you'll have to uncompress the data before you can restore it.

---

### Post by ZenMasta on 2010-05-24
I see and then what is the correct way to deploy the backup 

of=/dev/sdb1 
OR
of=/dev/sdb

Thanks.

---

### Post by gaussian on 2010-05-24
Couple things:
In order to restore the thing, you need to know if you originally "cloned" the partition (e.g. /dev/sda1) or the drive with (e.g. /dev/sda) with dd. I hope you did the whole drive, because otherwise you might have boot-sector issues.

Assuming that you did clone the whole drive you should be able to restore it with
```

gunzip -c image.gz | dd  of=/dev/sda

```

If it was just a partition, you should replace /dev/sda with /dev/sda1 (or whatever was the partition number)

Edit: obviously your device could be /dev/sdb or /dev/sdc. Do not run these commands unless you are 100% sure of the device!!!!!!

---

### Post by ZenMasta on 2010-05-25
Pretty sure I did the whole drive not just the partition. We'll soon find out. I unzipped before I left work so gonna try to restore it now. That's what I was thinkin anyway but after the few attempts yesterday not knowing I had to unzip first I was unsure.

---

