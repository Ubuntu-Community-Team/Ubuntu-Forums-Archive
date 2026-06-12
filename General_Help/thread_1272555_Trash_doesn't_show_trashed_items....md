---
title: "Trash doesn't show trashed items..."
date: 2009-09-22
forum: General Help
---

### Post by coldReactive on 2009-09-22
When in trash:/// I find that whatever I delete doesn't show up in the trash. This happens randomly with new installs of ubuntu. Sometimes it works, sometimes it doesn't. Is there any way to fix it?

---

### Post by louieb on 2009-09-22
If your running nautilus with gksudo then deleted items will show up in roots ./local/trash folder.

---

### Post by coldReactive on 2009-09-22
> **louieb said:**
> If your running nautilus with gksudo then deleted items will show up in roots ./local/trash folder.

I'm not though.

---

### Post by dankdave on 2009-09-22
are you deleting stuff through nautilus or with rm from the command line?  rm kills your files immediately.

---

### Post by coldReactive on 2009-09-22
> **dankdave said:**
> are you deleting stuff through nautilus or with rm from the command line?  rm kills your files immediately.

Nope, through nautilus/delete key.

---

### Post by credobyte on 2009-09-22
Reinstall Nautilus.

```
sudo apt-get reinstall nautilus

```

---

### Post by coldReactive on 2009-09-22
> **credobyte said:**
> Reinstall Nautilus.

```
sudo apt-get reinstall nautilus

```

```
E: Invalid operation reinstall
```

---

### Post by credobyte on 2009-09-22
> **coldReactive said:**
> ```
E: Invalid operation reinstall
```

```
sudo apt-get install --reinstall nautilus
```

Still the same error ? :-k

---

### Post by coldReactive on 2009-09-22
Now my trash works, after restarting, thanks. If I have the problem again, I'll just do that again I guess.

---

