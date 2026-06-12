---
title: "Delete Azureus folder"
date: 2009-09-22
forum: General Help
---

### Post by jaka on 2009-09-22
Is this correct command for delete folder rm /home/jaka/.azureus?

---

### Post by geirha on 2009-09-22
No.
This will remove the directory if it is empty
```
rmdir /home/jaka/.azureus
```

This will remove the directory and everything in it. Be VERY careful that you type the right directory.
```
rm -rf /home/jaka/.azureus
```

If you want to do it from nautilus (the file browser), hit Ctrl+H to toggle showing hidden files, then mark the directory and delete it.

---

### Post by jaka on 2009-09-22
Thank you very much.

---

