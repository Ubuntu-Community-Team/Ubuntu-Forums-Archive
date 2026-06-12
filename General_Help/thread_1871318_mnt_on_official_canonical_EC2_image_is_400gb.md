---
title: "/mnt on official canonical EC2 image is 400gb??"
date: 2011-10-28
forum: General Help
---

### Post by sneakyimp on 2011-10-28
OK so I've had my Amazon EC2 instance up for a couple of months now and just noticed that there appears to be a device, sdb, that is 400GB. What on earth is this device and can I use it? I instantiated this EC2 instance from one of the official canonical ubuntu images which said that the image was only 8GB (which is now completely full). If anyone could help me figure this out, I would be most grateful.

root@ip-WW-XX-YY-ZZ:/home/user# df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 7.9G 7.2G 311M 96% /
none 3.7G 112K 3.7G 1% /dev
none 3.8G 0 3.8G 0% /dev/shm
none 3.8G 68K 3.8G 1% /var/run
none 3.8G 0 3.8G 0% /var/lock
none 3.8G 0 3.8G 0% /lib/init/rw
/dev/sdb 414G 199M 393G 1% /mnt 

This is confusing to me because we are talking about virtual hardware rather than real stuff.  It's also confusing because my understanding of linux device management is somewhat limited (what does "none" mean, for instance).  Given that I need storage space for my growing apache logs, I need something that is real and reliable.  

Also, it's urgent.  As you can see my hard drive is more or less completely full.

---

