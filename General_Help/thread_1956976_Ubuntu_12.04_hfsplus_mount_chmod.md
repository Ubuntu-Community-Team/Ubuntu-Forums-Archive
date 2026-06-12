---
title: "Ubuntu 12.04 hfsplus mount chmod"
date: 2012-04-11
forum: General Help
---

### Post by thinktyler on 2012-04-11
I've read all of the ubuntu docs, but either I don't understand what is needed to be done, or somehow my external hard drive is different.

First I installed some HFSPLUS programs:

```
apt-get install hfsplus hfsutils hfsprogs
```

However, the external HD (WD 1tb) was mounting read-only fine at ubuntu's startup.

```
sudo mount -o force /dev/sdb1 /home/tdhz77/Desktop/Media/
```

and then tried
```
sudo mount -o remount,force,rw /mount/point
```

However, the only option that seems to work is:
```
chmod -R 777 *
```

But, Upon restarting I have to run the command again.

Any suggestions? Would this be solved in fstab?

---

