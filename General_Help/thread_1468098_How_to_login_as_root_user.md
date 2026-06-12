---
title: "How to login as root user"
date: 2010-05-01
forum: General Help
---

### Post by akssps011 on 2010-05-01
Hi i was trying to execute the following on Kubuntu.

```
echo 0 > /proc/sys/vm/vdso_enabled
```

But it says "permission denied". Probably I need root user rights. How to get it in Kubuntu?

---

### Post by Elfy on 2010-05-01
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

use sudo for non graphical or kdesudo

---

### Post by akssps011 on 2010-05-01
> **forestpiskie said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

use sudo for non graphical or kdesudo

I tried 

```
sudo echo 0 > /proc/sys/vm/vdso_enabled
kdesudo echo 0 > /proc/sys/vm/vdso_enabled
```

but both of them give "Permission denied"

---

### Post by dracayr on 2010-05-01
```
$sudo -s
#

```

EDIT: You could also do ```
sudo sh -c "echo 0 > ..."
```

---

### Post by lisati on 2011-12-27
Old thread closed.
The only way of gaining "root" access that is directly supported in this forum has already been mentioned: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

