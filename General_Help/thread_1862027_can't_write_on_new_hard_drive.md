---
title: "can't write on new hard drive"
date: 2011-10-16
forum: General Help
---

### Post by Acradon on 2011-10-16
Hello all, 

I just installed my new hard drive (a second one since I ran out of room on my old one). I manage to get it to automatically mount, but somehow I can't write anything on it. I have no permission. I can create files on it using the sudo command in the terminal, but how do I change the permissions to allow writing on it?

Greetz Acradon

---

### Post by Lars Noodén on 2011-10-16
If you're not going to be sharing it with other users, you can assign ownership to your account:

```

sudo chown -R acradon /path/to/new/disk

```

If you're going to be sharing with other users, then group permissions need to be set instead.

---

### Post by Acradon on 2011-10-16
Thank you Sir, 

worked like a charm.

---

