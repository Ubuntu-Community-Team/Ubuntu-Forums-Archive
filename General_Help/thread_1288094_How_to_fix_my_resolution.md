---
title: "How to fix my resolution?"
date: 2009-10-10
forum: General Help
---

### Post by mimat on 2009-10-10
I recently installed ubuntu over again,beacuase i accidently got rid of it now even after installing the drivers i cant get my native resoltion of 1440x900 someone help me please? =]

---

### Post by rippin on 2009-10-11
> **mimat said:**
> I recently installed ubuntu over again,beacuase i accidently got rid of it now even after installing the drivers i cant get my native resoltion of 1440x900 someone help me please? =]

Check your /etc/X11/org.conf and edit as needed or write one:

(sudo dpkg-reconfigure xserver-xorg)

---

