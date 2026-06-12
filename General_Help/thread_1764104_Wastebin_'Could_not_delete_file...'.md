---
title: "Wastebin: 'Could not delete file...'"
date: 2011-05-21
forum: General Help
---

### Post by ronniet on 2011-05-21
I seen to have several files that are 'stuck' in my Kubuntu 11.04 (KDE4.6.2) wastebin.

Whenever I try to empty the wastebin I get the message:
'*Could not delete file /home/ronnie/.local/share/Trash/files/<filename>*'

I think it's because one/more of the files has unusual characters in the filename.

Is there a way to manually empty the wastebin?

I've tried Shift+Del and also forcing KDE to delete files after seven days. Two weeks later and the files are still in the wastebin.

**Any ideas?** :confused:

---

### Post by ambdeep on 2011-05-21
try running:
```
sudo rm *path to file*
```

---

### Post by ronniet on 2011-05-21
> **ambdeep said:**
> try running:
```
sudo rm *path to file*
```

... almost! ;)

```
sudo rm -r <directory>
```

did it.

**Thanks for the nudge in the right direction though!**

---

