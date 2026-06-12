---
title: "Ubuntu doesn't recognize external hard drive?"
date: 2010-08-12
forum: General Help
---

### Post by cAlpha on 2010-08-12
Hard drive is connected to my Inspiron 1525 via USB, plugged in and I'm not seeing the new drive mounted.  Restart doesn't fix things and manually trying to mount /dev/sdb1 doesn't work either.  

The drive I got is preformatted as NTFS and I've been using a logical partition formatted as NTFS as a sort of share drive between my Windows partition and Ubuntu partition, so I know I have NTFS set up properly.  

[This]("http://accessories.us.dell.com/sna/productdetail.aspx?sku=A3563226&cs=19&c=us&l=en&dgc=CJ&cid=24471&lid=566643&acd=10550055-1225267-u0t2156028f30fp37416c0s441") is the hard drive I'm working with for reference.  

What could be going on?

---

### Post by bobcollard on 2010-08-13
> **cAlpha said:**
> Hard drive is connected to my Inspiron 1525 via USB, plugged in and I'm not seeing the new drive mounted.  Restart doesn't fix things and manually trying to mount /dev/sdb1 doesn't work either.  

The drive I got is preformatted as NTFS and I've been using a logical partition formatted as NTFS as a sort of share drive between my Windows partition and Ubuntu partition, so I know I have NTFS set up properly.  

[This]("http://accessories.us.dell.com/sna/productdetail.aspx?sku=A3563226&cs=19&c=us&l=en&dgc=CJ&cid=24471&lid=566643&acd=10550055-1225267-u0t2156028f30fp37416c0s441") is the hard drive I'm working with for reference.  

What could be going on?
Install ntfs-config from Synaptic Package Manager.

---

### Post by cAlpha on 2010-08-13
> **bobcollard said:**
> Install ntfs-config from Synaptic Package Manager.


Did that and launching it, the new drive isn't recognized (only the recovery partition that I haven't yet mounted is listed).

---

### Post by bobcollard on 2010-08-13
> **cAlpha said:**
> Did that and launching it, the new drive isn't recognized (only the recovery partition that I haven't yet mounted is listed).
See this post for reference of similar incident, don't know if you can get help from it or not.
[http://ubuntuforums.org/showthread.php?t=1551533](http://ubuntuforums.org/showthread.php?t=1551533)

---

