---
title: "whats better for data safety in 10.04: ext3 or ext4?"
date: 2010-05-08
forum: General Help
---

### Post by fbs777 on 2010-05-08
i need to chosse between ext3/ext4 but i dont know wich is better in this 10.04 version.
In my case dont matter the performance, just to avoid the data loss after power fail.

the system will not have any type of log, will be almost static, but i need to know if the ext3 still is better to avoid data loss

---

### Post by DeMus on 2010-05-08
> **fbs777 said:**
> i need to chosse between ext3/ext4 but i dont know wich is better in this 10.04 version.
In my case dont matter the performance, just to avoid the data loss after power fail.

the system will not have any type of log, will be almost static, but i need to know if the ext3 still is better to avoid data loss

Since the beginning of Ext 4 I have used it, I think it was when Jaunty came in April last year. I have never had any problems with it. I think it is safe to say Ext 4 is pretty safe and, not unimportant, faster than Ext 3.

---

### Post by fbs777 on 2010-05-08
> **DeMus said:**
> Since the beginning of Ext 4 I have used it, I think it was when Jaunty came in April last year. I have never had any problems with it. I think it is safe to say Ext 4 is pretty safe and, not unimportant, faster than Ext 3.
im not sure, but old versions like jaunty was using an ext4 version w/ a serious bug about data loss after power fail. for those who every time turn off correctly dont have any problem...

and the system that i will use must to work ok after many times of power fail.

thats why i want to know if the new 10.04 is using an ext4 w/ this bug w/ power fail fixed.

---

### Post by Manyette on 2010-05-08
Please understand that this is just one mans opinion, but I just did a reinstall with ext3, and while I've had no problem with ext4, there are many tools (gparted, clonezilla) which have not yet been updated to deal with ext4, so that was my reason for going back.  YMMV

---

### Post by aysiu on 2010-05-08
Both GParted and CloneZilla support Ext4.

---

### Post by Manyette on 2010-05-08
I see a recent addition to clonezilla that says it now support ext4, however partimage specificaslly says that is does NOT support ext4, and I rather thought that clonezilla depended on that in some instances.  What is there I don't know?

---

### Post by aysiu on 2010-05-08
> **Manyette said:**
> I see a recent addition to clonezilla that says it now support ext4, however partimage specificaslly says that is does NOT support ext4, and I rather thought that clonezilla depended on that in some instances.  What is there I don't know?
Sure, PartImage doesn't, but GParted certainly does. I've made, resized, and deleted Ext4 partitions with GParted and had no problems whatsoever.

---

### Post by Manyette on 2010-05-08
My error, but I was specifically wanting to use clonezilla, which depends on partimage, and that is why I dropped ext4.  By error, I typed gparted when I meant partimage.  Anyway, that was my reasoning.  As I saidf, YMMV.

---

