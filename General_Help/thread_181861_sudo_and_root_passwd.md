---
title: "sudo and root passwd"
date: 2006-05-24
forum: General Help
---

### Post by gumara on 2006-05-24
some user posible to run command sudo. he can run "$sudo passwd root". it's not good for root account. 

how to disable command "$passwd root" in that user?

---

### Post by cskeide on 2006-05-24
Don't think you can disable only the passwd root command. But you can remove the user from the admin group, and he/she will not be able to use sudo.
```
sudo deluser username admin
```
Replace "username" =)

---

