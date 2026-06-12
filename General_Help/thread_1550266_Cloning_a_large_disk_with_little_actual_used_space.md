---
title: "Cloning a large disk with little actual used space"
date: 2010-08-10
forum: General Help
---

### Post by meg23 on 2010-08-10
I need to clone a laptop drive to a desktop drive. The laptop drive disk is 150 gb, however, only about 8 gb is used. Is it possible to clone this disk to a smaller drive?

---

### Post by mike555 on 2010-08-10
If you shrink it .(the partition that is )

---

### Post by meg23 on 2010-08-10
Aside from the typical disclaimers, is it possible to shrink the root partition using the livecd?

---

### Post by linux18 on 2010-08-10
> **meg23 said:**
> Aside from the typical disclaimers, is it possible to shrink the root partition using the livecd?
yes
run this command in the drive you want to shrink before you use the livecd to shrink it a little more:

```
 sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean  
```

---

