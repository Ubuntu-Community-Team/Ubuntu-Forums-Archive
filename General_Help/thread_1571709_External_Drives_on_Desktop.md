---
title: "External Drives on Desktop"
date: 2010-09-10
forum: General Help
---

### Post by Vishnu V on 2010-09-10
Hi
 Is it possible to show only mounted external volumes  on the desktop. I try the method of uncheck /app/nautilus/desktop/volumes_visible. But it hides both internal and external disk.

Thanks

---

### Post by M93 on 2010-09-10
u can use 'ubuntu tweak' to do that
```
sudo apt-get install ubuntu-tweak
```

---

### Post by Vishnu V on 2010-09-10
Sorry I don't find any option to do that in the ubuntu-tweak 
Please tell me the option to do it
Thanks

---

### Post by TNT1 on 2010-09-10
> **Vishnu V said:**
> Sorry I don't find any option to do that in the ubuntu-tweak 
Please tell me the option to do it
Thanks

Under the "Desktop Icons" settings, there is an option to "show mounted volumes on desktop"....

---

### Post by Vishnu V on 2010-09-10
> **TNT1 said:**
> Under the "Desktop Icons" settings, there is an option to "show mounted volumes on desktop"....
This option shows both internal and external drives.I don't want to show mounted internal drives on the desktop. I just need to show only mounted **external drives** 
Thanks

---

### Post by dcstar on 2010-09-10
> **Vishnu V said:**
> This option shows both internal and external drives.I don't want to show mounted internal drives on the desktop. I just need to show only mounted **external drives** 
Thanks

External drives show on the desktop by default when this gconf key is set:

/apps/nautilus/desktop/volumes_visible

---

### Post by TNT1 on 2010-09-10
> **Vishnu V said:**
> This option shows both internal and external drives.I don't want to show mounted internal drives on the desktop. I just need to show only mounted **external drives** 
Thanks

Something is wrong with a gconf key of yours then, cause mine only shows external drives...

chaeck the post here regarding:
External drives show on the desktop by default when this gconf key is set:

/apps/nautilus/desktop/volumes_visible

---

