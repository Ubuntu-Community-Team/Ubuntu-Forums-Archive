---
title: "how to edit sudoers file"
date: 2011-05-16
forum: General Help
---

### Post by slaz on 2011-05-16
Hi, 
 
I want to create a group called scripts, add www-data to that group. I then want to edit the sudoers file and tell it that the script group doesn't need a password. Where should I put this line excatly in the sudoers file? Can I do it this way?
 
Any reply thanks,
slaz

---

### Post by garvinrick4 on 2011-05-16
[]("https://help.ubuntu.com/community/RootSudo")read OP wrong

---

### Post by bodhi.zazen on 2011-05-16
Use visudo

visudo checks the syntax and warns you of errors.

```
sudo visudo
```

---

