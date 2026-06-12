---
title: "Can't change plymouth theme for login, works on logout"
date: 2010-05-16
forum: General Help
---

### Post by chaosx9 on 2010-05-16
Well, basically, i've use the code

```
sudo update-alternatives --config default.plymouth
```

to change the plymouth theme, but it only changes the theme for logout, not for startup.

Does anyone know what to do?

---

### Post by dcstar on 2010-05-16
> **chaosx9 said:**
> Well, basically, i've use the code

```
sudo update-alternatives --config default.plymouth
```

to change the plymouth theme, but it only changes the theme for logout, not for startup.

Does anyone know what to do?

Try:

```
sudo update-initramfs -k all -u
```

---

### Post by Delvien on 2010-08-15
I can confirm this works. 

What was happening is that you are booting into 1-2 versions back from the most current kernel on your system, and when you update-initramfs -u, it only picks the highest kernel version. 

Therefore only updating the splash for a kernel you aren't even booting into.

---

