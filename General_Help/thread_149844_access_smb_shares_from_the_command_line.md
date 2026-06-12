---
title: "access smb shares from the command line?"
date: 2006-03-24
forum: General Help
---

### Post by vayu on 2006-03-24
Is there a way to access smb shares from the command line without mounting the share?

I tried the same address that works in Konqueror:

```

cd smb://username@hostname/sharedir

```

But it was a no go. "No such file or directory"

---

### Post by nemin on 2006-03-25
[QUOTE=vayu]Is there a way to access smb shares from the command line without mounting the share?[/QUOTE]
Perhaps `smbclient` is where you're looking for?

---

