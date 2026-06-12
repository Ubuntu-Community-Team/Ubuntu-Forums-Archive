---
title: "Cannot write to new SATA drive"
date: 2009-12-31
forum: General Help
---

### Post by AndrewS on 2009-12-31
Hi

I just put a second SATA drive in my PC.  Ubuntu (9.10) recognises it, but the owner is root and I therefore cannot copy files to it (without assuming su rights), although the permissions of the directory say that "Others" can read and write.  How do I change the ownership of the whole new drive to myself?  I've tried various permutations of chwon without success.

TIA

Andrew

---

### Post by Mud.Knee.Havoc on 2009-12-31
The command is chown, not chwon (that could be your problem right there!).  To change the ownership of the whole drive, you'll need to do it recursively.  Try this, inputting your own information into the parts with brackets:
 
sudo chown -R [user] [target]

If you want a graphical way to do it, just type
sudo nautilus
and change permissions with that.

---

### Post by AndrewS on 2009-12-31
Thanks for the reply.  "chwon" was a typo in my thread!

I tried to use nautilus, but got the following error:

[INDENT]Sorry, could not change the owner of "sda1": Error setting owner: Read-only file system[/INDENT]

Andrew

---

### Post by john newbuntu on 2009-12-31
Does opening it as "gksudo nautilus" help?

---

### Post by danastasio on 2009-12-31
> **john newbuntu said:**
> Does opening it as "gksudo nautilus" help?

No that won't help if the filesystem is read-only.

you -MIGHT- have to log in as root to gain write access. If you choose to do this, disable your network card. I would save this as a last resort though.

---

### Post by drs305 on 2009-12-31
I just installed a new hard drive last night. Here is what I did:

Created partitions, formatted them with Gparted, and labeled the partition (data2).

Made a new mount point for the partition I was interested in, made myself the owner of the mountpoint, and allowed access to others:
```

sudo mkdir /mnt/data2
sudo chown -R me: /mnt/data2
chmod 755 -R /mnt/data2  # Change as desired

```

Added to fstab:
```

gksu gedit /etc/fstab

```
> 
LABEL=data2 /mnt/data2  ext4 	defaults,users 	0 2

Saved the file, unmounted the partition (sdc2) then mounted it via fstab:
```

sudo umount /dev/sdc2
sudo mount -a

```
No messages means it was mounted correctly.

---

