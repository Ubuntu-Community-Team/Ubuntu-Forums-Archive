---
title: "Where is the data on Wubi installation?"
date: 2012-04-24
forum: General Help
---

### Post by duanecwilson on 2012-04-24
I am fairly new with Wubi/Ubuntu. I had to uninstall Wubi from my Windows 7 laptop and I am afraid the data, documents, and photos went with the uninstall. I am wondering where the data is/was stored? It is said that you can uninstall just like any other Windows installation. But every other Windows installation has a separate place for data. I cannot find any information anywhere on this subject. All I want to know is the basics of the file/folder structure.

---

### Post by Gremlinzzz on 2012-04-24
I would check my program folder :popcorn:

---

### Post by bcbc on 2012-04-25
The data is on the virtual disk(s) (usually just the file \ubuntu\disks\root.disk which is from 5GB to 30GB in size). This file is deleted when you uninstall. So the data is gone.

---

### Post by Mark Phelps on 2012-04-25
> **duanecwilson said:**
> But every other Windows installation has a separate place for data. I cannot find any information anywhere on this subject. All I want to know is the basics of the file/folder structure.

Unfortunately, it's not actually a Windows "installation" in where it stores data; instead, it uses Windows to install itself into a large file -- root.disk.

As mentioned, once that file is removed, everything associated with it is gone as well.

---

