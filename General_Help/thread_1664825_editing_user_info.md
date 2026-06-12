---
title: "editing user info"
date: 2011-01-11
forum: General Help
---

### Post by mattman85 on 2011-01-11
Is there a way to add my full name to my user account? I see how to add a user with a full name using:

```
sudo useradd -c “Full Name” -m -s “/bin/bash” usename
```

and I've seen that if I delete my user account, and create a new one with the same UID/GID, that it would have access to my files. Is this the way to go?

---

### Post by sisco311 on 2011-01-11
Check out:
```
man chfn
```

You have to run something like:
```
sudo chfn -f "New Full Name" **username**
```

---

### Post by mattman85 on 2011-01-11
Thank you! Excatly what I needed!

---

