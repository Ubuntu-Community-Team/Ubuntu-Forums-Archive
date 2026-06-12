---
title: "Can't get screenshot....."
date: 2006-01-21
forum: General Help
---

### Post by adam.tropics on 2006-01-21
Since the latest kernel upgrade, although i am not convinced of a connection, i am unable to get a screenshot. If i try i get,

> Details: Failed to execute child process "gnome-screenshot" (No such file or directory)

Any ideas?

---

### Post by 23meg on 2006-01-21
What errors do you get when you type "gnome-screenshot" in a terminal?

---

### Post by adam.tropics on 2006-01-21
command not found

---

### Post by 23meg on 2006-01-21
Install the gnome-utils package if it's not installed.

---

### Post by adam.tropics on 2006-01-21
Fantastic, thankyou. Confused though because until yesterday, screenshots were not a problem. anyway, all working now.

---

### Post by 23meg on 2006-01-21
It seems the update somehow removed gnome-utils; it's a good habit to keep an eye on which packages the update manager, Synaptic or apt-get are prompting to remove before doing updates, especially when you mix and match repositories.

---

### Post by adam.tropics on 2006-01-21
thanks for advice. btw does synaptic automatically store log files of such things?

---

### Post by 23meg on 2006-01-21
Yes; check out File / History.

---

