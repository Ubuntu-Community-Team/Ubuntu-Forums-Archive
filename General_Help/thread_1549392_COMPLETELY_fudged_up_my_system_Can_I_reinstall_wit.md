---
title: "COMPLETELY fudged up my system: Can I reinstall without losing data?"
date: 2010-08-09
forum: General Help
---

### Post by antdgar on 2010-08-09
My filesystem (software RAID 0):

Filesystem......            Size.......       Used.......          Avail.......      Use%.......      Mounted on
/dev/md1........              9.7G.......     2.8G.......           6.5G.......       31%.......       /
tmpfs........                 999M.......       0.......                999M.......      0%.......        /lib/init/rw
udev........                   10M.......                          2.7M       .......7.4M.......     27%....... /dev
tmpfs.......                 999M.......        0              .......999M.......        0%.......      /dev/shm
/dev/md3.......              901G.......    .......744G.......          112G.......        87%.......     /home

I don't have physical access to this machine. It is in a data center.

Can I reinstall the OS without losing the data in /home?
I can reinstall the OS. But my question is if there's a way to keep the /home directory and its data?

---

### Post by bergfly on 2010-08-09
Your /home is separate to the root so you are in luck. All you need to do is reinstall into the /dev/md1 partition. When you get to the partitioning part of the installer, do it manually and select /dev/md1 as your /, and format this, then select /dev/md3 as your /home and you will be gold. Do not check the format this partition box for /home, obviously! You may have some issues if you have many users in the /home folder as you will need to recreate them, but as long as you use the same main user, you should have access to fix this.

---

### Post by pricetech on 2010-08-09
It's still best to back up the contents of the home folder if that's possible.

---

