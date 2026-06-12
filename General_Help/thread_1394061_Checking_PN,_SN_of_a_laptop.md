---
title: "Checking P/N, S/N of a laptop"
date: 2010-01-30
forum: General Help
---

### Post by Lockheed on 2010-01-30
The label with those numbers on the bottom of my HP laptop has been totally worn down so I am unable to read them. Is there a command I can use to check those under linux?

---

### Post by Lockheed on 2010-01-30
**lshw**

---

### Post by lisati on 2010-01-30
```
sudo dmidecode
```

---

### Post by coldraven on 2010-01-30
Press F2 or possibly F10 when booting up and go into the BIOS setup utility.
The serial number should be listed there.

---

