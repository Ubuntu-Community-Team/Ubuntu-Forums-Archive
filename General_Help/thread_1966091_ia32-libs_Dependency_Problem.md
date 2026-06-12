---
title: "ia32-libs Dependency Problem"
date: 2012-04-26
forum: General Help
---

### Post by ShareBuntu on 2012-04-26
When I try to install ia32-libs I get an error that says I have an unmet dependency on ia32-libs-multiarch. However, when I try and install ia32-libs-multiarch, I get the same message, except this time the dependencies are gstreamet0.10-plugins-good, libcurl3, and libssl. Any ideas how I could resolve this and install ia32-libs?

---

### Post by ShareBuntu on 2012-04-26
If it's any help, here are the packages deborphan produced:

libgssdp-1.0-2
libaio1
libssl0.9.8
libcapi20-3
libisccc60
libsdl-net1.2
libc6-i386
libdns69
libcdio10
libodbc1
libmpg123-0
libgail-common
nautilus-dropbox
unity-2d-places
libxp6
unity-2d-launcher
libstdc++5

---

### Post by ShareBuntu on 2012-04-26
sudo install -f ia32-libs fixed it.

---

### Post by Cariboo1938 on 2012-04-29
> **ShareBuntu said:**
> sudo install -f ia32-libs fixed it.

Hi, it does not work:

> jg@JG-Laptop:~$ sudo install -f ia32-libs 
install: invalid option -- 'f'


---

### Post by pbrane on 2012-04-29
I think it should be 
```

sudo apt-get -f install ia32-libs

```

the **-f** attempts to fix broken packages

---

### Post by ShareBuntu on 2012-04-29
> **Cariboo1938 said:**
> Hi, it does not work:
Sorry! I have an alias for install. It should be sudo apt-get -f install ia32-libs. pbrane is correct.

---

### Post by forrestcupp on 2012-04-29
I don't think you should have to mess with this at all. 12.04 comes with multiarch preinstalled, which completely replaces ia32-libs. It's a new way of dealing with 32-bit software.

---

### Post by ShareBuntu on 2012-04-29
> **forrestcupp said:**
> I don't think you should have to mess with this at all. 12.04 comes with multiarch preinstalled, which completely replaces ia32-libs. It's a new way of dealing with 32-bit software.
It happened after an upgrade from 11.10 to 12.04. Didn't have the same problem on a clean install.

---

