---
title: "missing items/disc space...."
date: 2012-05-29
forum: General Help
---

### Post by tvradict on 2012-05-29
My root drive is partitioned at 91GB.  Currently there is only 91mb of free space and there are 347,406 Items.  I have looked for these items everywhere and simply cannot find them.

I struggle to believe an installation of 11.10 and a dozen installed programs can take up 91GB.  All of my personal files are held on a separate partition.

Does anyone have any idea where these files could be and how I can reclaim this space?

Thanks
Stuart

---

### Post by tvradict on 2012-05-29
Now I'm really confused....

GParted shows my root partition is only 6.25GB with 5.88GB used.

Any ideas why I'm being shown 91GB used when this is only 6GB to begin with?!

Cheers

---

### Post by oldos2er on 2012-05-29
Can you run these two commands in a terminal and copy and paste all the output here? ```
sudo fdisk -l

df -h
```

---

### Post by Fraoch on 2012-05-29
I had problems like this recently.  Did you move a lot of items in the Trash as root?

Things get really crazy if you move items to the Trash as root.  Never, ever do this.  Unfortunately I don't recall the exact sequence of events I used to fix it as I was panicking because I had no disk space and the OS was failing.  I seem to recall I had to delete items in the /root/.local/share/Trash folder.  Don't just delete them as that will move them to Trash, creating a vicious cycle, shift+delete them to wipe them completely.

Note - the Disk Usage Analyzer didn't show these files at all.  It just skipped over the /root/.local/share/Trash folder and showed the other folders, which looked normal.

---

### Post by tvradict on 2012-05-29
> **oldos2er said:**
> Can you run these two commands in a terminal and copy and paste all the output here? ```
sudo fdisk -l

df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.2G  5.8G   63M  99% /
udev                  1.4G  4.0K  1.4G   1% /dev
tmpfs                 555M  956K  554M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.4G  1.6M  1.4G   1% /run/shm
/dev/sda1             220G   86G  123G  42% /media/a8735213-dfc4-4f41-9ece-d8533dd71b5c


My first post was incorrect, my root partition is definitely 6GB not the 91GB I first said, however I will take 15GB from /sda1 and at it to /sda5

I cant understand why the root folder when right click > properties reports file size as 91GB.

---

