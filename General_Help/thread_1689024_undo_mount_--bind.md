---
title: "undo mount --bind"
date: 2011-02-16
forum: General Help
---

### Post by c2tarun on 2011-02-16
I mounted a folder on another by mount --bind. 
Can anyone please tell me how to undo it?

---

### Post by anglican on 2011-02-16
> **c2tarun said:**
> I mounted a folder on another by mount --bind. 
Can anyone please tell me how to undo it?```
sudo umount /mount/point
```where obviously /mount/point is the location you have mounted the folder. This won't work if /mount/point is your current directory or if any application has a file in /mount/point open. You'll need to change directory and/or close the file before you can unmount.

H

---

