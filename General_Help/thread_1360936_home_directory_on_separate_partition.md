---
title: "home directory on separate partition"
date: 2009-12-21
forum: General Help
---

### Post by phran on 2009-12-21
I have a separate partition for my home directory, but the o.s. doesn't point to it as the home directory.  (The o.s. points to the system partition for the home directory.)  How do I get the o.s. to point to the separate partition as the home directory?  Thanks.

---

### Post by drs305 on 2009-12-21
> **phran said:**
> I have a separate partition for my home directory, but the o.s. doesn't point to it as the home directory.  (The o.s. points to the system partition for the home directory.)  How do I get the o.s. to point to the separate partition as the home directory?  Thanks.

Place an entry in /etc/fstab to point to the /home partition. Something like this, replacing **sda6** with your /home partition designation and **ext4** if it's formatted to ext4 rather than ext3 Even better, use the UUID of the partition, which you can get with *sudo blkid*:
```

cp /etc/fstab /etc/fstab.bak  # Create backup copy
gksu gedit /etc/fstab
```
> 
/dev/[COLOR="Red"]sda6[/COLOR] /home [COLOR="Red"]ext3[/COLOR] nodev,nosuid 0 2

or
> 
[COLOR="Red"]UUID=269d31ae-24c9-451a-a71b-8224e355168b [/COLOR] /home [COLOR="Red"]ext3[/COLOR] nodev,nosuid 0 2


Make the changes, save the file, then reboot for the change to take effect.

---

### Post by phran on 2009-12-21
worked perfectly.  thanks!

---

