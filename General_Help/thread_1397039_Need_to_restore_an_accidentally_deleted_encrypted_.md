---
title: "Need to restore an accidentally deleted encrypted EXT4 partition"
date: 2010-02-02
forum: General Help
---

### Post by TehBleachBottle on 2010-02-02
I accidentally deleted my root ext4 partition, which I had encrypted. I am unable to log into any os since I am blocked by a Error 17. Is it possible to retrieve an encrypted ext4 partition, does it even matter that it was encrypted, and how do I go about fixing this?

---

### Post by bodhi.zazen on 2010-02-02
How did you "delete" it ?

How was the partition configured LUKS ? did you use LVM ?

---

### Post by TehBleachBottle on 2010-02-02
I run a dual boot with windows and I was using the disk management tool to try and increase its size a bit. Essentially I ended up just deleting it. No formatting though.

---

### Post by bodhi.zazen on 2010-02-02
If you know the exact disk geometry you can try to manually configure it or you could try testdisk.

run testdisk on a live CD, it is in the repositories

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by TehBleachBottle on 2010-02-02
What exactly do I need to find with the disk geometry? I mean I'm quite sure my live cd's could find that out but I don't have the courage to mess with some of those setting.

---

### Post by Leppie on 2010-02-02
if you haven't altered anything after deleting the parition and the only operation performed was deleting, testdisk will most probably be able to retrieve the geometry automatically.
if not at first, you can do a deep scan.

---

### Post by bodhi.zazen on 2010-02-02
> **TehBleachBottle said:**
> What exactly do I need to find with the disk geometry? I mean I'm quite sure my live cd's could find that out but I don't have the courage to mess with some of those setting.

If you do not know it I highly suggest you try testdisk.

The only problem may be that I am not sure how testdisk works with LUKS or LVM (I have not tried it).

---

