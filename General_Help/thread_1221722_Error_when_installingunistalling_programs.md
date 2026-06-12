---
title: "Error when installing/unistalling programs"
date: 2009-07-24
forum: General Help
---

### Post by Vihosa on 2009-07-24
So when I install/uninstall programs, I get a error message: "E: ttf-dejavu-extra: subprocess post-installation script returned error exit status 1" The programs work, but I've never experienced this.

---

### Post by wojox on 2009-07-24
Try:

```
sudo defoma-reconfigure -f
```

Ubuntu uses Defoma, the Debian Font Manager, to centralize and simplify font management across all applications.

---

### Post by Vihosa on 2009-07-24
> **wojox said:**
> Try:

```
sudo defoma-reconfigure -f
```Ubuntu uses Defoma, the Debian Font Manager, to centralize and simplify font management across all applications.
Thanks, it worked! :P

---

### Post by wojox on 2009-07-24
Welcome :D

---

