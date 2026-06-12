---
title: "Access Content of Window hard drive on Ubuntu?"
date: 2010-09-02
forum: General Help
---

### Post by FrustratedPerson on 2010-09-02
I installed Ubuntu within (along side) windows, But ubuntu is only showing me the 17GB that was dedicated to Ubuntu in My Computer. Is there a way to access everything on the hard drive even the stuff that's on the Windows 7 side?

---

### Post by lmarmisa on 2010-09-02
Do you see the Windows 7 disk partitions below Places?.

---

### Post by FrustratedPerson on 2010-09-02
No, that is not available.  Also, is it possible to increase the size I have allotted to Ubuntu? During the installation I left it to its default 17GB, now I wish I had made it 170 GB.

---

### Post by coffeecat on 2010-09-02
> **FrustratedPerson said:**
> I installed Ubuntu within (along side) windows

Do you mean within or alongside? To me, within suggests a wubi installation and alongside suggests a conventional dualboot with Ubuntu on its own partition. Horses of a entirely different colour.

If you mean within = Wubi, then you'll find your Windows C: in /host. Go to Places > Computer. Double-click on "File System". Open the host folder.

---

