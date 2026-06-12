---
title: "Adding new hdd to /home"
date: 2009-12-20
forum: General Help
---

### Post by lemmy999 on 2009-12-20
I currently have a 160gB disk on my desktop. Home is on a 140 gig partition and I have about 25% free space left. I have another 120gB drive that I would like to add to /home to increase the free space.

Is this possible and, if it is , how do I go about doing it?

---

### Post by nikhilbhardwaj on 2009-12-20
what takes up the most space in /home

one way could be 
create a mount point in the /home directory

say /home/yourusername/disk
add an fstab entry
with this as the mount point

---

### Post by lemmy999 on 2009-12-20
I have the usual suspects- music, films and about 30 distros!

---

### Post by SecretCode on 2009-12-20
What's the output of 
```
du --max-depth 1 ~ | sort -n | tail -n 10
```


As nikhilbhardwaj says, you could move one or more large subfolders to the new drive and create mount points under your home tree. The details depend on whether you need to move just one subfolder or a few.

---

### Post by dcstar on 2009-12-20
> **lemmy999 said:**
> I currently have a 160gB disk on my desktop. Home is on a 140 gig partition and I have about 25% free space left. I have another 120gB drive that I would like to add to /home to increase the free space.

Is this possible and, if it is , how do I go about doing it?

You may want to consider LVM:

[http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/)
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)
[http://www.linuxconfig.org/Linux_lvm_-_Logical_Volume_Manager](http://www.linuxconfig.org/Linux_lvm_-_Logical_Volume_Manager)

---

### Post by SecretCode on 2009-12-21
Good point. I don't use LVM but actually this kind of situation is exactly what it's for.

---

