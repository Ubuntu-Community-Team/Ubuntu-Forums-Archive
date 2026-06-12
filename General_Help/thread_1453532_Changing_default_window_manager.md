---
title: "Changing default window manager"
date: 2010-04-13
forum: General Help
---

### Post by jf812 on 2010-04-13
Im running Ubuntu and i installed kubuntu-desktop. When i installed it it asked me which one i wanted as the default (KDE or Gnome). I chose KDE and it also takes over the login screen and when my computer starts i get the kubuntu loading screen. How can i change it back to Ubuntu/Gnome?

---

### Post by Dans564 on 2010-04-13
Logout then u will see a session button click that then gnome and log in

---

### Post by jf812 on 2010-04-13
> **Dans564 said:**
> Logout then u will see a session button click that then gnome and log in

I know how to get into Gnome but it isn't the default + the login manager and boot loadup screen is for Kubuntu/KDE. I want to change it back to Ubuntu

---

### Post by philinux on 2010-04-13
> **jf812 said:**
> I know how to get into Gnome but it isn't the default + the login manager and boot loadup screen is for Kubuntu/KDE. I want to change it back to Ubuntu

```
sudo dpkg-reconfigure gdm
```

---

### Post by jf812 on 2010-04-13
> **philinux said:**
> ```
sudo dpkg-reconfigure gdm
```

Thanks

---

