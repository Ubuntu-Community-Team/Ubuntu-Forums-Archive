---
title: "Can I tell what motherboard I have?"
date: 2009-06-27
forum: General Help
---

### Post by irv on 2009-06-27
Is there a command I can use to find out what motherboard my system has without opening the case?

---

### Post by TeoBigusGeekus on 2009-06-27
```
sudo lshw > /home/username/Desktop/sys.info
```
It will save your system info in a file on your desktop.

---

### Post by hyperdude111 on 2009-06-27
Go to the website from the manufacturer and check the specs of your model.

---

### Post by irv on 2009-06-27
> **TeoBigusGeekus said:**
> ```
sudo lshw > /home/username/Desktop/sys.info
```
It will save your system info in a file on your desktop.

Thanks, that's what I was looking for.

---

