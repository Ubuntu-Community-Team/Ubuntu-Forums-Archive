---
title: "After having removed Windows 7 os..."
date: 2009-12-27
forum: General Help
---

### Post by Lazylazylazy on 2009-12-27
I have this massive space that I want to use but cant. I can't merge the partition to the main one.

How do I merge SDa2 and sda5 together and still have swap?
Also How do I decrease swap to 500mbs?

---

### Post by Lazylazylazy on 2009-12-27
bump

---

### Post by asqn34 on 2009-12-27
hi
you need to use a live cd and from there work on your partition.
as you want to resize your root partiton you need to do it outside your normal boot environment. 
Live cd and gparted are the tool.

---

### Post by Lazylazylazy on 2009-12-27
I can't move sda2 to the right of sda4.... That's my problem. I know I have to do it on USB boot

---

### Post by 3rdalbum on 2009-12-27
Your /dev/sda5 is inside an Extended partition. Extended partitions can't be resized or merged with non-Extended partitions.

You could erase the whole hard disk and install Ubuntu again with the partitioning scheme that you want.

What I would do in this case: you could move the contents of /home to /dev/sda2 (which apparently is currently mounted inside /media), and then add a new entry to /etc/fstab that mounts /dev/sda2 into /home; so effectively your 75 gigabyte partition becomes your /home.

You can still create folders inside / and put (for instance) your entire music collection in there, to use some of that extra space.

---

### Post by Lazylazylazy on 2009-12-27
@3rdalbum
sounds great! So there is hope after all, I don't wanna download the packages and backed up files from the net when I reinstall.
What do I add that new entry at etc/fstab?

---

### Post by 3rdalbum on 2009-12-27
Open a file browser and go to /home and then copy the folder(s) you see to the partition that's going to be your new home directory. Don't just copy the files from your own personal home directory, copy the whole folder structure in one hit, so your partition looks exactly like the /home.

Add the following to the bottom of your /etc/fstab file (you can open this file for editing by typing 'gksudo gedit /etc/fstab' into the terminal).

```
/dev/sda2 /home           ext4    defaults        0       2
```

Those are tabs in between each item.

Save your changes, reboot and you're done.

---

### Post by Lazylazylazy on 2009-12-27
Will give this a try tommrorow morning. Will update with reesults. Thanks.

---

### Post by 3rdalbum on 2009-12-27
> **Lazylazylazy said:**
> Will give this a try tommrorow morning. Will update with reesults. Thanks.

No worries, please send me a private message if you need more help with this (and post to the forums too as I might not be online).

---

### Post by Lazylazylazy on 2009-12-27
I think something went wrong. I could not put the /home folder in the 80 gig partition, because it said I wasn't the owner, then I did the /fstab edit with your script then rebooted.

ubuntu didn't boot properly, it said It could not find a config file, I couldn't see my desktop, my panels and icons and the wallpaper was the default one.

What now?

---

### Post by Lazylazylazy on 2009-12-27
Bunp

---

