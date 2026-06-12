---
title: "Change the name of Home folder"
date: 2010-07-08
forum: General Help
---

### Post by aum11 on 2010-07-08
I have successfully changed the username , but now I want to change the name of Home to reflect the new username.

Suggestions please.

---

### Post by nemilar on 2010-07-08
You could just use a symbolic link, so that nothing which depends on the old path breaks.

```
sudo ln -s /home/old_name /home/new_name
```

Now both /home/old_name and /home/new_name will point to /home/old_name.

---

### Post by aum11 on 2010-07-09
Thanks.  

However, this does not change the name for home when looking in Nautilus.

Is there some way I can change the name of Home to my new userid?

Ta

---

### Post by nemilar on 2010-07-10
You should be able to change the home directory path in the "Users and Groups" administration utility....

---

