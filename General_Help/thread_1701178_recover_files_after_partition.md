---
title: "recover files after partition"
date: 2011-03-06
forum: General Help
---

### Post by manoharan on 2011-03-06
can any one say how to recover files after partition..

because i installed ubuntu today and i had shocked to see that i lost all ma data..

i had gave install along with windows during parition.. but i lost all the data..

pls any one help me please...:(

---

### Post by JRV on 2011-03-06
Can we see how you have your partitions set-up?

Open a terminal and run the command:
```
sudo parted
```

When the parted prompt comes up run the command:
```
print
```

And post the results.

---

### Post by vanadium on 2011-03-06
JRV, a more convenient way to display partitions would be
```

sudo fdisk -l

```
or if you prefer to use parted:
```

sudo parted -l

```

Indeed this may confirm whether you have overwritten your existing partitions. If that is the case, then "testdisk" will probably be your last hope to revover the partitions or at least some of its data.

---

