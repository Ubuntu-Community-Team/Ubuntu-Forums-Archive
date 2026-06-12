---
title: "list of ALL users"
date: 2011-04-19
forum: General Help
---

### Post by mynameisnotbob on 2011-04-19
Um this may seem like a stupid question considering what I'm doing, but I'm implementing some automatic security protocols on a ubuntu system, and I need to see a list of all users, including system ones. The reason for this is that I created a system user with a specific UID, and I forgot it. The 'user' command only lists the nonsystem users.

---

### Post by ttshivers on 2011-04-19
cat /etc/passwd will give you a very long list of all the users

---

### Post by coffeecat on 2011-04-19
```
cat /etc/passwd
```

... should give you all users including system ones.

---

### Post by mynameisnotbob on 2011-04-19
thank you

---

