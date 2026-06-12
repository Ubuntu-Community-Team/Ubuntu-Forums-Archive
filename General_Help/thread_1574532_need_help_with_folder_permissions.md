---
title: "need help with folder permissions"
date: 2010-09-14
forum: General Help
---

### Post by boarder428 on 2010-09-14
I'm trying to add images to my usr/share/backgrounds directory in Lucid and don't seem to have permissions to do so and cannot figure out how change permissions or access the folder as root!

---

### Post by Rychoo on 2010-09-14
```

gksudo nautilus

```

---

### Post by 3rdalbum on 2010-09-14
You wouldn't change the permissions - that causes a lowering of security policy, which is not good.

However, you can temporarily browse your filesystem as root:

```
gksudo nautilus
```

(the 'gksudo' part says "Run the following graphical program as root" - if nautilus was a terminal command, you would use "sudo" instead)

You can also install the "nautilus-gksu" package if you want. When you next log in after installing this package, you can right-click any folder or file and choose "Open as Administrator".

---

### Post by Vigh on 2010-09-14
enter terminal, enter the directory of the files you want to copy to destination direction

cd /home/"user"/backgrounds

sudo cp file1.png /usr/share/backgrounds

---

### Post by boarder428 on 2010-09-14
thanks for the quick answers!

---

