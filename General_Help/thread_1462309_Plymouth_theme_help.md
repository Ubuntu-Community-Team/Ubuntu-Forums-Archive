---
title: "Plymouth theme help"
date: 2010-04-25
forum: General Help
---

### Post by AZorin on 2010-04-25
Hello, I've recently created a Plymouth theme that is based on the regular Ubuntu 10.04 one, I only changed the colours and graphics. When I set it, it only shows the theme I have made during shutdown. When I start up my computer it shows the regular Ubuntu one.
Is there any way to show the same theme for both startup and shutdown?

Thanks in advance
AZorin

---

### Post by towheedm on 2010-04-29
The same happens with Usplash.  I have not played with Plymouth as yet.  This works for Usplash, may also work for Plymouth:
```
sudo update-initramfs -u
```

---

### Post by 98cwitr on 2010-04-29
...

---

### Post by AZorin on 2010-05-01
> **towheedm said:**
> The same happens with Usplash.  I have not played with Plymouth as yet.  This works for Usplash, may also work for Plymouth:
```
sudo update-initramfs -u
```
Thanks a million!

---

