---
title: "default parition setup"
date: 2010-05-18
forum: General Help
---

### Post by alecbenzer on 2010-05-18
What is the default partition setup that the ubuntu installer uses? Ie which directories get their own partitions (If I remember correctly by default it doesn't just throw everything onto one partition, assuming you're installing onto a fresh hard drive).

---

### Post by alecbenzer on 2010-05-19
bump? anyone know?

---

### Post by eriktheblu on 2010-05-19
Default has one data (/) partition, and a swap partition.

---

### Post by LanternInc on 2010-05-19
'/' - file system partition
'/home' - user partition
'swap' - is used when the amount of physical memory is full

---

### Post by alecbenzer on 2010-05-19
Hrm...that's odd, I remember the installer wanting to create more partitions for some of the dirs in /... though that might have been for an older version. Or maybe I'm just imagining things.

---

