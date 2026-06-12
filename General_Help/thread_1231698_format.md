---
title: "format"
date: 2009-08-04
forum: General Help
---

### Post by majikhotline on 2009-08-04
what program or commands can i use to format the 2nd hard drive

thx

---

### Post by theozzlives on 2009-08-04
GParted

---

### Post by wojox on 2009-08-04
```
sudo mkfs -t ext3 /dev/sdb1
```

Substitute "/dev/sdb1" with your own partition's path.

---

