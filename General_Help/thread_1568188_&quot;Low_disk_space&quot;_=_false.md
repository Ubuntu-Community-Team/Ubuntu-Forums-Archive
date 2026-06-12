---
title: "&quot;Low disk space&quot; = false"
date: 2010-09-04
forum: General Help
---

### Post by L2U2K2E on 2010-09-04
I am currently ripping my collection of CDs to my hard drive, and every time I try to add more ubuntu brings up the message: > **Low Disk Space**
You can free up disk space by removing unused programs or files, or by moving files to another disk or partition.
it also lists the disk space it believes is left.


This message came up a few times this morning, so I ran Gparted and expanded my /home partition. I now have 52GB of space free on this partition. How can I get ubuntu to fully recognize that this partition is actually larger? 

It does appear as the correct size in the disk utility, Gparted, system monitor and every other program I have looked at. This warning message is the only noticeable problem.


Edit: now don't I feel stupid? all fixed! thank you!

---

### Post by audiomick on 2010-09-04
Don't know for sure. Have you restarted since resizing?

---

### Post by L2U2K2E on 2010-09-04
> **audiomick said:**
> Don't know for sure. Have you restarted since resizing?
I resized from a liveCD, but I have not restarted since I booted after that. I will try it.

---

### Post by audiomick on 2010-09-04
No, probably wont make any difference then. Was just a thought, anyway. Don't think I can offer anything useful, I am afraid. Sorry...

---

### Post by sandyd on 2010-09-04
> **L2U2K2E said:**
> I am currently ripping my collection of CDs to my hard drive, and every time I try to add more ubuntu brings up the message: 
it also lists the disk space it believes is left.


This message came up a few times this morning, so I ran Gparted and expanded my /home partition. I now have 52GB of space free on this partition. How can I get ubuntu to fully recognize that this partition is actually larger? 

It does appear as the correct size in the disk utility, Gparted, system monitor and every other program I have looked at. This warning message is the only noticeable problem.
post the output of
```

df -h
```

---

### Post by L2U2K2E on 2010-09-05
> **carlee said:**
> post the output of
```

df -h
```
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              11G  9.9G     0 100% /
none                  1.5G  320K  1.5G   1% /dev
none                  1.5G  1.7M  1.5G   1% /dev/shm
none                  1.5G   92K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda2             107G   49G   53G  49% /home

```

---

### Post by L2U2K2E on 2010-09-05
Sorry to be annoying and bump this, but it causing quite a few problems. I cannot perform any updates.

---

### Post by gandaran on 2010-09-05
> **L2U2K2E said:**
> Sorry to be annoying and bump this, but it causing quite a few problems. I cannot perform any updates.
the root partition looks full not home, clean the download cache, it will release same space.
```
sudo apt-get clean
```

---

### Post by audiomick on 2010-09-05
> **L2U2K2E said:**
> ```

Filesystem            Size  Used Avail Use% Mounted on
[COLOR=Red]/dev/sda1              11G  9.9G     0 100% /[/COLOR]
none                  1.5G  320K  1.5G   1% /dev
none                  1.5G  1.7M  1.5G   1% /dev/shm
none                  1.5G   92K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda2             107G   49G   53G  49% /home

```
It is not your /home that is full, it is the system partition, the / . In your case sda1.

Don't be confused by the fact that only 9,9GB of 11GB is in use. What is not showing up is probably the system overhead, i.e. space that the file system uses for it's own purposes.

You could try moving some space from /home to /. (i.e. sda2 smaller and sda1 larger). I haven't done this myself recently, but believe it shouldn't cause you any grief.

As always with partitioning: if there is anything really important on the drive, back it up first.

---

