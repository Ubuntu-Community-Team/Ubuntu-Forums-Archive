---
title: "How to change partition size without loss of data?"
date: 2010-08-23
forum: General Help
---

### Post by saidbakr on 2010-08-23
Hi,
I have a partition mount to /boot of size equals to 50 MB. I would like to increase its size to 100 or 150 MB. **How could I change its size without the risk of getting data lost or the corruption of the Ubuntu installation on my computer?**

I have Ubuntu 10.04.

---

### Post by srs5694 on 2010-08-23
There is no 100% safe way to do this; however, if you're willing to accept some risk, you can use GParted, GNU Parted, or various other tools to resize your partitions. See [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html) for more detailed instructions. If you need more explicit help, you'll need to post more details, such as a screen shot of the GParted screen or the text-mode output of typing "sudo fdisk -l" on your system.

---

### Post by saidbakr on 2010-08-23
Hi,
Should it need to use Live CD?

---

### Post by Rubi1200 on 2010-08-23
> **saidbakr said:**
> Hi,
Should it need to use Live CD?
Basically, yes.

The reason being that the partitions need to be unmounted for tools like GParted to work more effectively.

The Ubuntu LiveCD has GParted installed; makes life easier.

In any event, you must backup your data first as there is always some risk involved when working with partitions/drives.

---

