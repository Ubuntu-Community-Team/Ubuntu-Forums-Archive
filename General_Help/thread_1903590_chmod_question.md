---
title: "chmod question"
date: 2012-01-02
forum: General Help
---

### Post by crutch145 on 2012-01-02
I would like to change access permissions to a folder that is owned by root.  I do not want to change ownership, I just want to modify the permission so that every user that falls into the "other" group cannot r/w/x a certain directory.  What command do I need to enter in the terminal to make this happen?  

Thanks,

Justin

---

### Post by fdrake on 2012-01-02
> **crutch145 said:**
> I would like to change access permissions to a folder that is owned by root.  I do not want to change ownership, I just want to modify the permission so that every user that falls into the "other" group cannot r/w/x a certain directory.  What command do I need to enter in the terminal to make this happen?  

Thanks,

Justin
```

sudo chmod o-xrw -R /my/directoy/path

```
note (-R) is for recursive to be applied to all files and subdirectories in the folder

---

### Post by Dangertux on 2012-01-02
> **crutch145 said:**
> I would like to change access permissions to a folder that is owned by root.  I do not want to change ownership, I just want to modify the permission so that every user that falls into the "other" group cannot r/w/x a certain directory.  What command do I need to enter in the terminal to make this happen?  

Thanks,

Justin

```

sudo chmod 640 filename

```

Will yield read/write for the owner, read for the group and nothing for anyone else. Alternatively 

```

sudo chmod 750 filename

```

Will give read write exec to owner, read exec to group and nothing to everyone else.

Or 

```

sudo chmod 770 filename

```

will give rwx to the group and user but nothing to world.

Hope this helps.

---

### Post by sisco311 on 2012-01-02
Please don't try to change the permissions of a system file/directory. What exactly are you trying to accomplish?

---

### Post by crutch145 on 2012-01-02
I should have reworded my question... I falsely assumed I wanted to block access to the "other" group, but that is not the case.  I have my backup drive (spare hard drive) automatically mounted to /media/backup upon system bootup.  I only want my user account to have access to the /media/backup directory.  I created a guest user account... however, when I login as guest, it has full access to /media/backup.  I do not want guest to have access to this directory, because it contains a backup of all my personal documents.  Root is the owner of /media/backup... which is why I need to know what terminal command I need to use deny access to the guest user account.

---

