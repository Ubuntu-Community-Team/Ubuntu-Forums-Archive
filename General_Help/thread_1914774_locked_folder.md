---
title: "locked folder"
date: 2012-01-25
forum: General Help
---

### Post by hotshot247 on 2012-01-25
i have a folder that's locked so i can't delete it as a regular user but when i try to sudo the folder to delete it, it says that it cannot delete it because it's a read only file system. how can i change it to where it's not just read only? thanks

---

### Post by dcstar on 2012-01-25
> **hotshot247 said:**
> i have a folder that's locked so i can't delete it as a regular user but when i try to sudo the folder to delete it, it says that it cannot delete it because it's a **read only file system**. how can i change it to where it's not just read only? thanks

Make the file system not "read only".

---

### Post by hotshot247 on 2012-01-25
> **dcstar said:**
> Make the file system not "read only".

REALLY...is that what you have to do, lol i was asking HOW to set it to where it's not read only.

---

### Post by jerrrys on 2012-01-25
In terminal:

gksudo nautilus

Then navigate to the folder and pull up properties (contex menu) and change.

That what you looking for?

---

### Post by Frogs Hair on 2012-01-25
Right click the file and enter properties > permissions  to change  folder properties .

---

