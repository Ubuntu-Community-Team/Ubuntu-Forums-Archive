---
title: "Converting ext3 to ext4 on an installed system ?"
date: 2010-11-18
forum: General Help
---

### Post by uncle-c on 2010-11-18
Hi,
I've recently installed Ubuntu 10.10 on a machine, unfortunately, the hard drive was ext3 partitioned. Is there a way of converting this partition to ext4 without having to re-format and hence reinstall the entire OS ?

---

### Post by jpl888 on 2010-11-18
Short answer yes.

Slight longer answer yes but existing files won't be upgraded to extents until they are re-written, so you won't get all the performance benefits until this happens.

Info here is as good as most on how to do it.

[http://www.kev009.com/wp/2008/12/how-to-upgrade-to-ext4-in-place/](http://www.kev009.com/wp/2008/12/how-to-upgrade-to-ext4-in-place/)

---

### Post by uncle-c on 2010-11-18
Thanks.

---

### Post by jpl888 on 2010-11-18
You're welcome.

---

### Post by psusi on 2010-11-18
> **jpl888 said:**
> Short answer yes.

Slight longer answer yes but existing files won't be upgraded to extents until they are re-written, so you won't get all the performance benefits until this happens.

Info here is as good as most on how to do it.

[http://www.kev009.com/wp/2008/12/how-to-upgrade-to-ext4-in-place/](http://www.kev009.com/wp/2008/12/how-to-upgrade-to-ext4-in-place/)

Actually you can use chattr to enable extents on a/all file(s).

You also won't get the fsck speed up from upgrading.

---

