---
title: "Another no widescreen resolution issue"
date: 2010-12-20
forum: General Help
---

### Post by Rogy on 2010-12-20
Hello,

I installed Ubuntu 10.10 along side windows 7, It works flawlessly accept for one issue: no widescreen resolution (1440x900)

I have some CIBOX screen and XFX HD 6850.


Any way to fix the widescreen issue?

---

### Post by psihokiller4 on 2010-12-20
System --> Preferences --> monitors

does that help you anyhow?

don't exactly understand your question

---

### Post by Rogy on 2010-12-20
The only resolutions I get to choose from are: 
1400 x 1050 (4:3)
1280 x 1024 (5:4)
1280 x 960 (4:3)
1152 x 864 (4:3)
1024 x 768 (4:3)
800 x 600 (4:3)
640 x 480 (4:3)
720 x 400 (9:5)

There are no widescreen resolutions

---

### Post by sikander3786 on 2010-12-20
Which graphics card is there?

Applications > Accessories > Terminal:

```
lspci | grep VGA
```

Did you activate the graphics drivers (if available)? System > Administration > Additional Drivers.

---

