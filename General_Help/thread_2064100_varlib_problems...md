---
title: "var/lib problems.."
date: 2012-09-28
forum: General Help
---

### Post by EkiLibRiuM on 2012-09-28
helo to everybody i have some problem whit my Ubutu i have installed and run program's everything it' working but some directory are blocked or i don't have permisssion to access on them...i am using a virtual Ubuntu...thanks for you help..the var/lib directory i's blocked...best regards.

---

### Post by drmrgd on 2012-09-28
Locations like /var (pretty much everywhere but a user's home directory!) are protected from modification in order to prevent system problem and security breaches.  In order to modify these areas you need to have superuser or root privileges.  So, if you need to modify a file or folder in /var/lib, you must either prefix your command with 'sudo' when using the terminal:

```
sudo cp /var/lib/<somefile> /some/location/<somefile>
```

Or launch a file manager (e.g. Nautilus) with elevated permissions:

```
gksudo nautilus
```

Hope that helps

---

### Post by EkiLibRiuM on 2012-09-28
Thank 's a lot ofr your explanation..i am glad to be here ans get some help for the first time in my live ..God bless you..

---

