---
title: "Clone a hard disk (or partition) and tell how long will it take"
date: 2010-09-11
forum: General Help
---

### Post by GeoMX on 2010-09-11
I often need to clone hard disk or partitions at work, I use several software for this: dd, cp, gparted. But none of them indicates an estimate for the total time it'd take for the full operation to complete (gparted indicates it on a per operation basis and only shows the time it took after completion).

Is there another software that can clone a hard disk and indicate an estimate of the time it will take?

Thanks.

---

### Post by JBAlaska on 2010-09-11
I know Clonezilla's "clone to remote" has a time to completion function, not sure about the local to local mode though.

---

### Post by Lukas666 on 2010-09-11
Do you need an exact time? May I ask why? When I clone my 1TB HDD I just start the process and go out. But it never takes more than 2 hours.

Can you provide more details?

---

### Post by howefield on 2010-09-11
Acronis True Image

However, it is commercial application and I haven't used it since support for ext4 was limited to sector by sector cloning, it may be different now. 

Doesn't matter because Clonezilla ftw, it will tell you how long to completion of the current operation/partition, but I am not sure about total time to complete, ie a disk with more than one partition.

---

### Post by GeoMX on 2010-09-13
I'll try Clonezilla, thanks a lot for the info :).

We clone hard disks everyday, estimate time for the cloning operation to complete is useful for performance tests, tasks scheduling and reports. We currently use an old Norton Ghost version, but would like to try a more recent software that could take advantage of newer hardware.

---

### Post by howefield on 2010-09-13
> **GeoMX said:**
> We currently use an old Norton Ghost version,...

In that case, there is every chance you'll feel right at home with Clonezilla. :)

---

### Post by GeoMX on 2010-09-23
I've just tried Clonezilla and to my surprise it is very slow: it took about five hours to clone a 500 GB disk which Ghost clones in about two and a half.

I started it from an USB, but think it has nothing to do with this poor performance.

Thanks for your help.

---

