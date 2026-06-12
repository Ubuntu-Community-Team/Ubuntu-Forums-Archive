---
title: "How do I share files between Ubuntu and XP"
date: 2009-06-25
forum: General Help
---

### Post by Zorrorrorro on 2009-06-25
Hi there,

Essentially, I want Ubuntu to see folders in XP and access them and vice versa.

How do I go about doing this? I have Ubuntu 8.04 LTS and 9.10.

Thank you!!!!

Zorrorrorro

---

### Post by bodhi.zazen on 2009-06-25
Easiest way is to do it with samba. Samba works out of the box.

Right click on a directory in Ubuntu -> share -> follow directions.

[Setting Up Samba - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by Nepherte on 2009-06-25
To access maps shared by Windows, you need the smbclient package. To share maps from ubuntu, you can use samba (see [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) for more information).

---

### Post by Megrimn on 2009-06-25
I've been doing it a different way.  In Ubuntu, I just mount the windows partition, but unfortunately Windows *cannot see* the ubuntu partition.

---

### Post by bodhi.zazen on 2009-06-25
> **Megrimn said:**
> I've been doing it a different way.  In Ubuntu, I just mount the windows partition, but unfortunately Windows *cannot see* the ubuntu partition.

Ah, you are right. For some reason I got the impression the OP was asking how to access network shares.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by fugaki on 2009-06-25
> **Megrimn said:**
> I've been doing it a different way.  In Ubuntu, I just mount the windows partition, but unfortunately Windows *cannot see* the ubuntu partition.

You can get ext3 drivers for windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Megrimn on 2009-06-25
> **fugaki said:**
> You can get ext3 drivers for windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Sweet! thanks!

---

