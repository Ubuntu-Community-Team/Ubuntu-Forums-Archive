---
title: "missing disk space"
date: 2011-10-04
forum: General Help
---

### Post by tachyon4 on 2011-10-04
I recently repartitioned my hard drive (I moved "/" and then grew it).  My partition manager tells me that the partition grew (and has little free space), but it seems (from the file browser, xdiskusage, etc) that my partition is still the size it was before the operation.  "df -h" yields

```
/dev/sda4              11G  9.7G  485M  96% /
none                  1.5G  368K  1.5G   1% /dev
none                  1.5G  188K  1.5G   1% /dev/shm
none                  1.5G  292K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
```

plus some other stuff (/media/...).  My old partition size was 11G, and my new partition size should be 18.5G (11+1.5+1.5+1.5+1.5+1.5).  What's going on, and what can I do to make all 18.5G accessible?

---

### Post by mcduck on 2011-10-04
That sounds you just grew the partition, without growing the filesystem inside it to fill the additional space.

This should do the trick:
```

sudo resize2fs /dev/sda4
```

---

### Post by tachyon4 on 2011-10-05
It worked.  Thanks.

---

