---
title: "How to remove/correct partially installed packages?"
date: 2010-08-30
forum: General Help
---

### Post by boffti on 2010-08-30
Im currently running Ubuntu netbook 10.04 on my Acer aspire one. My problem is that when i try to install something from the software centre, its says that the previous packages werent installed properly and i have to correct or remove them. How do I correct or remove them? The thing is that i dunno which packages they are?!

---

### Post by Bachstelze on 2010-08-30
Try

```
sudo apt-get -f install
```

---

### Post by boffti on 2010-08-30
thanks! it worked.

---

