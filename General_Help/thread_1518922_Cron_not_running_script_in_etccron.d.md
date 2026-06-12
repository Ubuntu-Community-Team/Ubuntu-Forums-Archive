---
title: "Cron not running script in /etc/cron.d/"
date: 2010-06-27
forum: General Help
---

### Post by Arenlor on 2010-06-27
I have the following saved in /etc/cron.d/
-rw-r--r-- 1 root root  30 2010-06-26 11:11 clearswap
The contents if it is:
0 * * * * /usr/sbin/clearswap
Which contains a modified version of the clearswap script found in Ubuntu's SwapFAQ:
```
#!/bin/bash
# Clears the cache and buffers then empties the swap into RAM
# This MUST be run as root, not just under sudo
# Arenlor
err="Not enough RAM to clear swap."
sync
echo 1 > /proc/sys/vm/drop_caches
echo 2 > /proc/sys/vm/drop_caches
echo 3 > /proc/sys/vm/drop_caches
mem=`free|grep Mem:|awk '{print $4}'`
swap=`free|grep Swap:|awk '{print $3}'`
test $mem -lt $swap && echo -e $err && exit 1
swapoff -a && swapon -a && exit 0
```
Figured this out, I was using the cron format, should have been using crontab format. /etc/cron.d/clearswap should have been
0 * * * * root /usr/sbin/clearswap

---

