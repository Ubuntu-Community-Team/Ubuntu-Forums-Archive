---
title: "Clone /home partition to new larger drive"
date: 2009-08-26
forum: General Help
---

### Post by sjprice on 2009-08-26
So luckily I took some advice and set up my /home partition on a separate drive when I did a fresh install of 9.04. So now I would like to copy my /home partition to my new 1TB drive.

I understand I can use ```
dd if=/dev/sda1 of=/dev/sdb
``` once both drives are connected and using the correct /dev/sdX designations, but I have a feeling my system won't see the new /home partition when I unplug the old one.

What step am I missing? Also, when I use dd, do I still have to make a partition the same size of my current drive then use the live cd to expand it?

Thanks in advance.

---

### Post by oldfred on 2009-08-27
I do not have a separate /home but expect you to have a /home entry in /etc/fstab using the UUID. After you have created the partition and copied the data you can find the UUID using:
```
blkid
```

I would not think dd cares about partition sizes but am not sure. I use cp to copy stuff and dd when conversion like to iso is required but I am no expert on commands.

---

### Post by beastrace91 on 2009-08-27
You should just be able to copy over the /home to a new drive using GParted. Then as oldfred suggested just open up your /etc/fstab file and point it to the new location (whether you want to use your UUID or sdxx it doesn't matter) of ur new /home

~Jeff

---

