---
title: "Automatic Updates"
date: 2006-03-11
forum: General Help
---

### Post by scav on 2006-03-11
Hi, how can i make the update manager to upgrade the new packages automaticly, without asking the user.
Yeah, even when nobody logged in..

We are converting many pcs from windows to ubuntu at my school, and if we get it right, it might be permanently :)

therefore, keeping the pc's up to date is essential.

Greetings

---

### Post by Koybe on 2006-03-11
I don't know how to set this particular program. But you can do a script :

```
#!/bin/bash
apt-get update
apt-get -y dist-upgrade
```

And run it daily (as root) for example.

---

