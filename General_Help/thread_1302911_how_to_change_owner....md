---
title: "how to change owner..."
date: 2009-10-27
forum: General Help
---

### Post by mimoza on 2009-10-27
I'm trying to change owner for one directory. and I know I can go with the "chown", but I want to make that directory available for all of the users, not just for one in the group. (?)

---

### Post by mac666 on 2009-10-27
try instead

chmod 777 -r /directory/

Im not sure you are suppose to do this way, but this is how i do it :)

The -r is for doing 777 for all subfolders et c

---

### Post by MegaLoler on 2009-10-27
I think ```
chmod 777 <path to directory>
``` will work.

---

### Post by akakingess on 2009-10-27
> **MegaLoler said:**
> I think ```
chmod 777 <path to directory>
``` will work.

Yes, but won't that allow everyone access, instead of just everyone in a particular group? Say I wanted anyone in the admin group to have access, but not users (I know, not a great example, since admins could get into it anyway), but would something like sudo chown admin:admin work or not?

---

### Post by mimoza on 2009-10-27
uh... it does not go. i get...

```
chmod: cannot access `777': No such file or directory
```

...any other solutions?

---

### Post by mimoza on 2009-10-27
> **akakingess said:**
> Yes, but won't that allow everyone access, instead of just everyone in a particular group? Say I wanted anyone in the admin group to have access, but not users (I know, not a great example, since admins could get into it anyway), but would something like sudo chown admin:admin work or not?

I want for all of the users. So all can enter and change that folder

---

### Post by mimoza on 2009-10-27
oh, I haven't seen one of the replies. I tried with "-r" in it. :S
Thanks so much for help. :)

---

### Post by efflandt on 2009-10-27
Isn't it **chmod ugo +rwx /path/dir** (may need sudo in front of that)?

Although, I am not clear on the difference between small x and capital X on a dir.  See **man chmod**

---

