---
title: "Zenmap"
date: 2011-07-14
forum: General Help
---

### Post by ub45 on 2011-07-14
I've just installed Zenmap and was wondering could anybody show me how to get root access.

---

### Post by fdrake on 2011-07-14
in the terminal write:

```
sudo zenmap
```
enter password

---

### Post by ub45 on 2011-07-14
Hi fdrake I've typed the command and it worked the Zenmap starts up from there but when I click in the 
menu bar it tells me I'm non root user.

---

### Post by mikejonesey on 2011-07-14
gksu "zenmap %F"

---

### Post by fdrake on 2011-07-15
like the previous post says  [http://tokyoimage.wordpress.com/2010/12/22/how-to-launch-zenmap-as-root-from-the-ubuntu-applications-menu/]("http://tokyoimage.wordpress.com/2010/12/22/how-to-launch-zenmap-as-root-from-the-ubuntu-applications-menu/")


but when i run sudo zenmap from the terminal i don't get the root error like you.ehmm ??

---

