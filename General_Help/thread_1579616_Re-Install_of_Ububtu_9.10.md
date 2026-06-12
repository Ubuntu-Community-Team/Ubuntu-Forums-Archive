---
title: "Re-Install of Ububtu 9.10"
date: 2010-09-22
forum: General Help
---

### Post by cdo on 2010-09-22
Just reformatted and re-installed Ubuntu 9.10 on my computer . Update Manager says there are no updates available but also says package information was updated 328 days ago and that doesn't sound right to me .

In the process of downloading a 200+mb video i got a pop up window saying that the computer did not have sufficient storage to finish the download . Disk usage Analyser shows the following:

Total File System Capacity -  227.8Gb
Total File system Usage -        3.4 Gb -  1.5%

Anyone have any ideas about these two discrepancies ? 

Thanks

Edit: Ignore issue 1 as dummie on this end forgot to hit the "check" icon..   :-)

Issue # 2 still in play

---

### Post by Elfy on 2010-09-22
can you run and then post the data from the following command please

```
df -h
```

---

### Post by mr_luksom on 2010-09-22
I have to ask, why 9.10 and not 10.04?

---

### Post by cdo on 2010-09-22
> **mr_luksom said:**
> I have to ask, why 9.10 and not 10.04?

Because i have a 9.10 disk .  :)

---

### Post by cdo on 2010-09-22
> **forestpiskie said:**
> can you run and then post the data from the following command please

```
df -h
``` 

ubuntu@ubuntu:~$ df  -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  497M  394M  103M  80% /
udev                  497M  240K  496M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  497M  300K  496M   1% /dev/shm
tmpfs                 497M   12K  497M   1% /tmp
none                  497M   88K  496M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda1             227G  2.1G  213G   1% /target
ubuntu@ubuntu:~$ 

Is this indicating i had a bad install somewhere along the Line ? Update Manager also says i do not have enough free disk space:

Upgrade needs 682mb free space on '/' . Please free at least 604 mb of disk space on '/'  .

---

### Post by cdo on 2010-09-22
Problem Solved...  Thanks forest for the terminal command.

After looking at the terminal readout i discovered that the Ubuntu cd was stuck in the player and i had not noticed as the light was not on .  Apparently the cd was what Ububtu was reading instead of the hard drive ..  :-)

---

