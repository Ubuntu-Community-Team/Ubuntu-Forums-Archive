---
title: "Low Disk Space Warming - Ignore or not?"
date: 2012-02-12
forum: General Help
---

### Post by Quarkrad on 2012-02-12
Running 10.10.  Just run Bleechbit and had warning that **Filesystem root**  only had 256 bytes of disk space remaining - I chose to *Ignore* and I cleared out 1.5Gb of data. A little while latter I run Blechbit again (I know there's no point) and I get another warning - now I only have 0 bytes of disk space for my Filesytsem root (what ever that is?).  Thing is, I dual boot windoze and Ubuntu; Ubuntu is in it's own partition (everything - I do not have a separate partition for /home) and according to GParted the Ubuntu partition (/dev/sda2) is 97.55Gb with 61.83Gb spare.  With all this spare capacity how can I have a warning about disk space?  Hmm -title should read Warning - not Warming!

---

### Post by snowpine on 2012-02-12
If you open a Terminal and paste the following command, you'll get useful numbers, you can copy & paste back here to get help:

```
df -h
```

---

### Post by Quarkrad on 2012-02-12
Thanks - this is the output:

[B]dad@dadubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              97G   35G   57G  38% /
none                  2.0G  324K  2.0G   1% /dev
none                  2.0G  1.1M  2.0G   1% /dev/shm
none                  2.0G   88K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda3             263G  226G   38G  86% /media/store
/dev/sdb5             932G  638G  295G  69% /media/backup[/B]
dad@dadubuntu:~$ 

seems to me I have plenty of spare capacity.

---

### Post by snowpine on 2012-02-12
I agree.

Perhaps a Bleachbit expert will happen along and tell you why Bleachbit is giving that error. :)

---

