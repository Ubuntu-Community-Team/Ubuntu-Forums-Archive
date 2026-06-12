---
title: "mounting hard drives from Live CD"
date: 2006-06-05
forum: General Help
---

### Post by Amadomon on 2006-06-05
I am sure this is in here somewhere, but I just can't find it.  Could someone please tell me how to mount my hard drive from the Live CD?  I backed up my hard drive before it started dying, and I want to copy it over to my iPod, but I can't mount the hard drive.  Please help!  Thanks.

---

### Post by BitTorrentBuddha on 2006-06-05
```
sudo mkdir /mnt/rootpart
sudo mount /dev/hda1 /mnt/rootpart
```
This is assuming your "/' partition is located on the first partition of the first drive, if it's not change hda1 to whatever it is in the /dev directory.

---

### Post by Amadomon on 2006-06-05
thanks so much

---

### Post by Amadomon on 2006-06-05
hmm, actually, I get the msg that I must specify the filesystem type.

---

### Post by ivotedforkodos on 2006-06-09
[QUOTE=Amadomon]hmm, actually, I get the msg that I must specify the filesystem type.[/QUOTE]

I got the same error, but then I tried this:

```

sudo mkdir /mnt/rootpart
sudo mount -t ext3 /dev/hda2 /mnt/rootpart

```

but I get a different error. It says:

```

mount: wrong fs type, bad option, bad superblock on /dev/hda2, 
missing codepage or other error (aren't you trying to mount an extended 
partition, instead of some logical partition inside?) In some cases useful into is 
found in syslog - try dmesg | tail or so

```

So I did that, and it said: unable to read superblock, attempt to access beyond end of device" 

What can I do?

---

### Post by aysiu on 2006-06-09
Are you sure /dev/hda3 is ext3?

---

