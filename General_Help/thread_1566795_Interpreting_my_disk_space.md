---
title: "Interpreting my disk space"
date: 2010-09-02
forum: General Help
---

### Post by Pondoro on 2010-09-02
OK, I typed "df -h" and got this response:
mike@Aethelred:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              14G   11G  2.6G  80% /
none                  679M  284K  679M   1% /dev
none                  683M  428K  683M   1% /dev/shm
none                  683M   84K  683M   1% /var/run
none                  683M     0  683M   0% /var/lock
none                  683M     0  683M   0% /lib/init/rw
/dev/sda2             4.5G  1.8G  2.8G  39% /media/423B-2BDF
/dev/sdf1             7.4G  6.0G  1.5G  80% /media/MIKE'S IPOD

What is sda5 and what is sda2?

Thanks!

---

### Post by jerome1232 on 2010-09-02
Really your the one who set your partitioning scheme up, how can we know?

/dev/sda2 looks like just a small partition, probably fat32 based on the label name. 

/dev/sda5 is your root partition (you main system partition, in your case it's where all your stuff goes)

---

### Post by llawwehttam on 2010-09-02
sda 2 looks like a memory stick to me.

---

### Post by jerome1232 on 2010-09-02
That's what I thought as well at first, but it's sda, same disk as the root partition.

---

