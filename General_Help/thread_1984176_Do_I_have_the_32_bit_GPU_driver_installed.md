---
title: "Do I have the 32 bit GPU driver installed?"
date: 2012-05-21
forum: General Help
---

### Post by LunaticStrain on 2012-05-21
Hello all,

I am trying to find out what Nvidia driver I have installed, specifically if it is the 32 bit or the 64 bit driver. I have searched and found a dozen or so terminal commands to check on my graphics card information, but not one of them lets me know if it is 32 bit or 64 bit. Thanks for any help,

Billy.

---

### Post by rai4shu2 on 2012-05-21
For 12.04, the following command will tell you (if you're using the current driver):

```
apt-cache show nvidia-current | grep Arch
```

---

