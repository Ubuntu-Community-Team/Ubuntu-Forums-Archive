---
title: "how to set a path"
date: 2009-09-13
forum: General Help
---

### Post by gilm on 2009-09-13
Hi,
I've installed a new program package under /opt/new_package
Where should I update the PATH so that the executables under lets say /opt/new_package/bin will be found when I invoke them from bash command line.
Note, I need them to be available also when I invoke them using sudo <command> so the path should also be updated for the root user.
Thanks a lot,
Gil

---

### Post by x33a on 2009-09-13
add it to 
```
/etc/profile
```

find the line containing the path and add the changes there.

---

