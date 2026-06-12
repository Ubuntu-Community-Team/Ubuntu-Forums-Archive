---
title: "recovering HDD after irresponsible use of 'wipe'"
date: 2011-11-09
forum: General Help
---

### Post by m4lte on 2011-11-09
Hey folks,

I was about to securely erase a hard drive using wipe. However, I overdid it without reading the man pages first. I wiped the whole hard disk like this:

$ sudo wipe -qir /dev/sda
Okay to WIPE 1 special file ? (Yes/No) Yes
Not wiping special file /dev/sda in recursive mode
Renaming /dev/sda -> /dev ZrbSyn
Operation finished.

I guess I did exactly what they described as "extremely dangerous" in the man pages ([http://linux.die.net/man/1/wipe](http://linux.die.net/man/1/wipe)).
Now $ sudo fdisk -l does not show the disk anymore.
When I use $ sudo lshw -C disk it is listed, but as "UNCLAIMED". I attached a screenshot of the output.

What did I actually do to the hard drive and are there any ways that could possibly make it usable again?

Thanks for your help ;)


[B]EDIT:
Just rebooting ubuntu solved the problem. The disk was then shown in gparted again and I could just create a new partition table.[/B]

---

### Post by ajgreeny on 2011-11-09
Can you see it with gparted?  It may be that you have removed all of the partition table and therefore it is not showing in the system.  Gparted may be able to see it and make a new partition table.

PS:  I don't know wipe, so I could be totally wrong.

---

### Post by m4lte on 2011-11-09
> **ajgreeny said:**
> Can you see it with gparted?  It may be that you have removed all of the partition table and therefore it is not showing in the system.  Gparted may be able to see it and make a new partition table.

PS:  I don't know wipe, so I could be totally wrong.

unfortunately, gparted doesn't show the disk anymore

---

