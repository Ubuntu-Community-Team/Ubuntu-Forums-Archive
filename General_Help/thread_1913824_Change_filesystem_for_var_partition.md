---
title: "Change filesystem for /var partition"
date: 2012-01-23
forum: General Help
---

### Post by noMaster on 2012-01-23
Hi guy! I tried to change filesystem type for my */var* partition and got a trouble. I had reiserfs for */var*. And now I need jfs. I made backup a partition with *'tar -czpvf '*. Boot livecd and format a partition (jfs). Upload files back with *'tar -xvvf '* and change fstab. During boot I get an error about mounting issue. But when I repeat this chain with reiserfs again everthing looks good! :(

---

### Post by Lars Noodén on 2012-01-23
> **noMaster said:**
> ...*'tar -czpvf '*...*'tar -xvvf '* 

The -p option is needed during the extraction, too.  Same with -z.

---

### Post by noMaster on 2012-01-24
I used *'-xzpvf '* and recovery was successful. Cheer! Thank you! :D

---

### Post by eghost355 on 2012-09-10
> **noMaster said:**
> I used *'-xzpvf '* and recovery was successful. Cheer! Thank you! :D

I tried but fail. Pls help me to debug. 
My procedures are:

0) already has another non-system partition up and running
1) backup /var by "cd /var; tar -czfvp ~/var.tar.gz ./*" (or "rsync -axS /var/* ~/var/")
2) reboot to rescueCD
3) mkfs.jfs /dev/sdc1 (/var partition)
4) mount -o noatime -t jfs /dev/sdc1 /mnt/var
5) restore /var content by "tar -xvzfp ~/var.tar.gz -C /mnt/var" (or "rsync -axS ~/var/* /mnt/var")
6) update system's /etc/fstab to change /var to JFS
7) reboot back to linux

Then it eventually hangs at "System Logger" then load any further. No viewable error can be seen.

Anything I missed? Thanks! :(

---

