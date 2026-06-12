---
title: "Disk space disappearing for no apparent reason"
date: 2011-05-20
forum: General Help
---

### Post by SimenMM on 2011-05-20
I woke up this morning to a message saying I have low disk space in /home. My /home partition is 150 GB, but I had only 4 kB left. I promptly rebooted, which helped, but I still only have 40 GB available. Now, I use only 26 GB, so where the rest is, I don't know. In the disk usage analyzer, a lot of the space was not accounted for, as shown in the image.
[[IMG]http://s2.postimage.org/2zwa7412c/Screenshot_1.jpg[/IMG]]("http://postimage.org/image/2zwa7412c/")

Here is the output from df -h and du

simen@simen-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              55G  8.0G   45G  16% /
none                  2.0G  368K  2.0G   1% /dev
none                  2.0G  176K  2.0G   1% /dev/shm
none                  2.0G  204K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda6             150G  100G   43G  71% /home
/dev/sdb1             932G  477G  455G  52% /media/Elements_

simen@simen-laptop:~$ sudo du --human-readable --max-depth=1 /home
du: cannot access `/home/simen/.gvfs': Permission denied
100G    /home/simen
16K    /home/lost+found
54M    /home/tale
100G    /home

I checked out .gvfs and it's just a CD I have playing. I really don't know what's going on, could you guys help?

---

### Post by dcstar on 2011-05-20
> **SimenMM said:**
> I woke up this morning to a message saying I have low disk space in /home. My /home partition is 150 GB, but I had only 4 kB left. I promptly rebooted, which helped, but I still only have 40 GB available. Now, I use only 26 GB, so where the rest is, I don't know. In the disk usage analyzer, a lot of the space was not accounted for, as shown in the image.
.......

```
gksudo baobab
```

---

### Post by mcduck on 2011-05-20
Well, the space is being used in your own home directory, so you should just continue digging deeper with the with the "du" command to find out where exactly it's used.

You now scanned the /home, with depth of one, which was enough to tell that it's /home/simen where the space is used. So the next step would be to repeat the scan, this time in /home/simen:

```
du --human-readable --max-depth=1 /home/simen
```

---

### Post by SimenMM on 2011-05-20
Found it. What was confusing me was that there was no folder that accounted for all that space, and 
I couldn't find any file that did either. Turns out it was hidden, .xsession-errors.old. Thanks!

---

