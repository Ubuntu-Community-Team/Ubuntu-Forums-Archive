---
title: "DPKG Lock Error in Fresh Install"
date: 2006-06-28
forum: General Help
---

### Post by Luddy on 2006-06-28
Hello, I just installed Ubuntu 6.06 on my Dell Inspiron 6000 laptop.  The Live CD worked perfectly so I went ahead and installed it on a 25 GB partition.

To select and create the partitions I used the option that selected the largest contiguous free space.

It appeared to ahve installed fine, I was able to browse the internet even, but then I tried to install the system updates.  They all failed.  I tried to run easyunubunu it failed saying the DPKG Lock was in use.

I tried sudo apt-get update and got the same thing.

What could be the problem.  I tested apt-get update running off the Live CD it worked fine.  But after I install it to the HD it always says another package manager is running.  I looked in the system manager and see no process named 'aptitude', 'synaptic', or 'apt-get'.  Thanks for any help.  I would prefer a way to permanently fix this.  If I am really having a package manager conflict with the DPKG lock file.  Thanks for any help.

This is more or less the exact error message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

---

### Post by Luddy on 2006-06-28
I still get errors when I run in root.  Could it be a router/nat issue with the system updates?

I am able to browse the web via Firefox though.

edit - I guess what I was thinking was maybe the install of sudo apt-get update or the system update fails because of the router screws up the package manager.  Which prevents me from obtaining a lock after the fail.

---

