---
title: "Steps to reinstall kernel"
date: 2009-07-01
forum: General Help
---

### Post by Jestersage on 2009-07-01
Does anyone know what's the CLI steps to reinstall the Linux 2.26.28-11 kernel? For some reason, while it "claims" it is 9.04, uname -a and one other command gives out 2.26.27 (8.10) kernel), and that's also what stated during GRUB.

Thanks in advance.

---

### Post by RD1 on 2009-07-01
```
sudo apt-get install linux-image
```

This should get you up to 2.6.28.13.17

---

### Post by Jestersage on 2009-07-01
Thanks. That works.

---

### Post by RD1 on 2009-07-01
You are quite welcome! :popcorn:

---

