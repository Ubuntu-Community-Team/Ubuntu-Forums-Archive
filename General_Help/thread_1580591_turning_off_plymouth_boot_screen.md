---
title: "turning off plymouth boot screen"
date: 2010-09-23
forum: General Help
---

### Post by SimplySimon... on 2010-09-23
Hi there,

quite a while ago i decided i wanted to change my splash

---

### Post by andrewthomas on 2010-09-23
> **SimplySimon... said:**
> Hi there,

quite a while ago i decided i wanted to change my splash

Either your title, **turning off plymouth boot screen**,  is misleading, or your question is confusing.  

To turn off the plymouth boot splash, 

```
gksu gedit /etc/default/grub
```

and change  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to 
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
then 
```
sudo update-grub
```

---

