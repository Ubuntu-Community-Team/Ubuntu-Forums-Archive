---
title: "How to check installed video driver"
date: 2009-09-29
forum: General Help
---

### Post by b-boy on 2009-09-29
Hi Guys

How do I check what video driver my ubuntu 9.04 is using ?

---

### Post by StuartN on 2009-09-29
> **b-boy said:**
> How do I check what video driver my ubuntu 9.04 is using ?

```
lshw -class video
```

(list hardware of class video, the driver is listed near the end)

---

### Post by b-boy on 2009-09-29
> **StuartN said:**
> ```
lshw -class video
```

(list hardware of class video, the driver is listed near the end)

thanks

---

