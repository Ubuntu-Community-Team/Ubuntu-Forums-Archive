---
title: "How do I make a ramdisk?"
date: 2010-06-04
forum: General Help
---

### Post by 98cwitr on 2010-06-04
I want to load my ~/.cache and /tmp directories into a ramdisk every time I start my machine, so I added this to my fstab

```

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /home/brett/.cache tmpfs defaults,noatime,mode=1777 0 0
```

But I dont see hardly any memory utilization or processes that would indicate that this was successful

I do see when I run *df* the following lines

```


/dev/sda1             55292308  10633604  41849976  21% /
none                   1025696       276   1025420   1% /dev
none                   1030128      1892   1028236   1% /dev/shm
tmpfs                  1030128        12   1030116   1% /tmp
none                   1030128        92   1030036   1% /var/run
none                   1030128         0   1030128   0% /var/lock
none                   1030128         0   1030128   0% /lib/init/rw
tmpfs                  1030128      2248   1027880   1% /home/brett/.cache

```

Is that all that needs to be done or am I missing a step?

---

### Post by 98cwitr on 2010-06-05
anyone?

---

### Post by phr33k-dc on 2010-06-05
this could b what u are looking for.

[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

---

### Post by jocko on 2010-06-05
> **98cwitr said:**
> I want to load my ~/.cache and /tmp directories into a ramdisk every time I start my machine, so I added this to my fstab

```

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /home/brett/.cache tmpfs defaults,noatime,mode=1777 0 0
```But I dont see hardly any memory utilization or processes that would indicate that this was successful

I do see when I run *df* the following lines

```


/dev/sda1             55292308  10633604  41849976  21% /
none                   1025696       276   1025420   1% /dev
none                   1030128      1892   1028236   1% /dev/shm
tmpfs                  1030128        12   1030116   1% /tmp
none                   1030128        92   1030036   1% /var/run
none                   1030128         0   1030128   0% /var/lock
none                   1030128         0   1030128   0% /lib/init/rw
tmpfs                  1030128      2248   1027880   1% /home/brett/.cache

```Is that all that needs to be done or am I missing a step?
According to your df, you have accomplished what you want. Why would you expect any significant memory utilization from this? My /tmp normally uses only a few kb, and my ~/.cache is only a few Mb...

---

### Post by 98cwitr on 2010-06-05
> **jocko said:**
> According to your df, you have accomplished what you want. Why would you expect any significant memory utilization from this? My /tmp normally uses only a few kb, and my ~/.cache is only a few Mb...

I dont, just trying to verify what I've done is correctly config'd

---

### Post by sdennie on 2010-06-05
If df is reporting it mounted as tmpfs, you've accomplished what you want.  The reason that you may not see a difference in memory utilization is that tmpfs is treated as cached RAM backed by swap.  The only way to detect the difference in RAM usage would be to drop the caches via:

```

sudo sh -c "echo 1 > /proc/sys/vm/drop_caches"

```

And then comparing how much of the cache was still in memory both before and after moving things to tmpfs.

---

### Post by 98cwitr on 2010-06-05
> **sdennie said:**
> If df is reporting it mounted as tmpfs, you've accomplished what you want.  The reason that you may not see a difference in memory utilization is that tmpfs is treated as cached RAM backed by swap.  The only way to detect the difference in RAM usage would be to drop the caches via:

```

sudo sh -c "echo 1 > /proc/sys/vm/drop_caches"

```

And then comparing how much of the cache was still in memory both before and after moving things to tmpfs.

that's all I needed to know...thanks ya'll

---

