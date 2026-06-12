---
title: "Need to make a dummy file; what's the command?"
date: 2010-02-27
forum: General Help
---

### Post by ownaginatious on 2010-02-27
Hey guys,

I need to make a 10 GB dummy file of random numbers. I know it can be done with dd, but it always says I run out of memory (I'm assuming it means RAM) when I try to do so.

Does anyone know a command that will accomplish what I want?

Thanks!

---

### Post by Kakers on 2010-02-27
You mean?

```

dd if=/dev/zero of=testfile_10GB bs=10737418240 count=1

```

---

### Post by ownaginatious on 2010-02-27
Ya, but when I do that I receive the following error:

```
dd: memory exhausted
```

---

### Post by solitaire on 2010-02-27
Are you running this from a LiveCD?

---

### Post by Kakers on 2010-02-27
This might be a problem with the size on your swap space? can you give us a print out of your partitions?

```
sudo fdisk -l
```

Need to know how much RAM you have and HDD space.

---

### Post by falconindy on 2010-02-27
> **Kakers said:**
> You mean?

```

dd if=/dev/zero of=testfile_10GB **bs=10737418240** count=1

```
That's a surefire way to run yourself out of memory since data is cached as per the blocksize before being read/written. A more sane solution would be something like...
```
dd if=/dev/zero of=/path/to/out/file bs=1M count=1024
```

---

### Post by dcstar on 2010-02-27
> **falconindy said:**
> That's a surefire way to run yourself out of memory since data is cached as per the blocksize before being read/written. A more sane solution would be something like...
```
dd if=/dev/zero of=/path/to/out/file ***bs***=1M count=1024
```

***bs*** should be the optimum for writing each chunk of data to a device - 8192 is usually as big as you want to go for a hard disk.

Large ***bs*** sizes will do little but clog up RAM and slow down the actual write process by filling the write queue for that device.

---

### Post by falconindy on 2010-02-28
> **dcstar said:**
> ***bs*** should be the optimum for writing each chunk of data to a device - 8192 is usually as big as you want to go for a hard disk.

Large ***bs*** sizes will do little but clog up RAM and slow down the actual write process by filling the write queue for that device.
Normally, I'd agree with you, but the goal here is just to write out a giant file. To that end, the time theoretically saved by specifying an optimal block size is probably used up by doing the calculation to determine the block count.

---

