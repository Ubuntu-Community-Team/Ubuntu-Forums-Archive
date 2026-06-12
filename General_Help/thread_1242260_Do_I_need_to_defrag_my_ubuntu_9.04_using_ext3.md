---
title: "Do I need to defrag my ubuntu 9.04 using ext3?"
date: 2009-08-16
forum: General Help
---

### Post by cardinalsfan030 on 2009-08-16
i am fairly new to Linux, but I am loving it more and more everyday, I barley touch the "other operating system" any more.  I was just wondering if I have to defrag my hard drive at all?

---

### Post by lisati on 2009-08-17
With the ext3 file system commonly used in many Linux distributions there isn't the same need to defrag as there would be in Windows.

[http://en.wikipedia.org/wiki/Defragmentation](http://en.wikipedia.org/wiki/Defragmentation)

---

### Post by cardinalsfan030 on 2009-08-17
> **lisati said:**
> With the ext3 file system commonly used in many Linux distributions there isn't the same need to defrag as there would be in Windows.

[http://en.wikipedia.org/wiki/Defragmentation](http://en.wikipedia.org/wiki/Defragmentation)


Thanks for your reply, I didn't think you had to I just wanted to make sure

---

### Post by calc on 2009-12-07
If you use Transmission (bittorent) much you probably would need to defragment but the only easy way to do so on ext3 is to backup the partition then copy everything back. There is also a script that essentially the same thing somewhere here on the forum but I don't remember the thread id.

You can also switch to ext4 which doesn't fragment as often as ext3 and will eventually have a defrag program available for it.

---

### Post by kaibob on 2009-12-07
Post deleted by Kaibob. Just noticed that this is an old thread.

---

### Post by cybrsaylr on 2009-12-08
I've always been told there is no need to defrag Linux and that a defrag will cause damage to a Linux OS.

---

### Post by calc on 2009-12-10
> **cybrsaylr said:**
> I've always been told there is no need to defrag Linux and that a defrag will cause damage to a Linux OS.

Thats probably due to the fact that there was no defrag program available and people assuming it was because it wasn't needed, not just because no one had written one. Currently, to my knowledge, there are only defrag programs available for XFS and Ext4, and the Ext4 defrag program is still under development and not advised to be used on production systems. However the Ext4 defrag program might be safe to use by the time Lucid is released.

[https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22](https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22)

The only damage a defrag program, that is properly written, could do would be to flash based drives, like a SSD, since they have limited number of write cycles. The more you use a flash based drive the more likely it is to fail.

---

### Post by paradigm2 on 2009-12-10
> **calc said:**
> Thats probably due to the fact that there was no defrag program available and people assuming it was because it wasn't needed, not just because no one had written one. Currently, to my knowledge, there are only defrag programs available for XFS and Ext4, and the Ext4 defrag program is still under development and not advised to be used on production systems. However the Ext4 defrag program might be safe to use by the time Lucid is released.

[https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22](https://bugs.launchpad.net/ubuntu/+bug/321528/comments/22)

The only damage a defrag program, that is properly written, could do would be to flash based drives, like a SSD, since they have limited number of write cycles. The more you use a flash based drive the more likely it is to fail.

Thanks for the info.  I am looking forward to a polished and stable ext4 defrag utility.  Ext4 is one of the main reasons I jumped over to 9.10.

---

