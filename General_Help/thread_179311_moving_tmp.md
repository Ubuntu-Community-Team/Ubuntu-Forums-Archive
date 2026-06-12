---
title: "moving /tmp"
date: 2006-05-19
forum: General Help
---

### Post by fuzzymallets on 2006-05-19
What would be the best method to move the /tmp to another location.

What I am tring to do is move the /tmp from one hard drive to a larger RAID0 array.

---

### Post by eentonig on 2006-05-19
Create it on the other disk, and then mount it on the same location it was before. This way, application expecting /tmp, won't get confused.

---

### Post by aysiu on 2006-05-19
Are you trying to move the *contents* of /tmp, too (its temporary files), or just make it its own separate partition?

---

### Post by fuzzymallets on 2006-05-19
All i'm tring to do it move the location so that apps will use the /tmp on the raid.


eentonig, i dont appreciate the insult. I'm new to linux and tring to learn.

---

### Post by aysiu on 2006-05-19
[QUOTE=fuzzymallets]All i'm tring to do it move the location so that apps will use the /tmp on the raid.[/quote] In Nautilus, make note of /tmp's permissions and ownership. For this example, I'm going to assume it's owned by root and has 776 permissions. I would ```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
``` to format the new drive as Ext3 and make note of its location (I'm going to assume it's /dev/hdb1, but it may be something else). Then ```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Tack this line on at the end: ```
/dev/hdb1 /tmp ext3 defaults 0 0
``` The save (control-x), confirm (y), and exit (Enter). Then ```
sudo rm -rf /tmp/*
sudo mount -a
sudo chown -R root:root /tmp
sudo chmod -R 775 /tmp
```

> 
eentonig, i dont appreciate the insult. I'm new to linux and tring to learn. It's eentonig's signature, not her/his post that's offensive. It's not aimed specifically at you.

---

### Post by fuzzymallets on 2006-05-19
oh ok thx and I apologize eentonig. I didn't relize that was a signature. :oops:

---

### Post by aysiu on 2006-05-19
[QUOTE=fuzzymallets]oh ok thx and I apologize eentonig. I didn't relize that was a signature. :oops:[/QUOTE] The signature is still offensive... I just wanted to state that it wasn't directed at you.

---

