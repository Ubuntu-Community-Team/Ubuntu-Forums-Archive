---
title: "Nautilus Permissions"
date: 2010-05-11
forum: General Help
---

### Post by ubunterooster on 2010-05-11
Nautilus as root is on the left; nautilus as Ubunterooster (normal user) on the right

Screen-shot# 1, Permissions before I change them.

#2, after I change and hit "apply to enclosed files" before clicking the button labeled "close".

#3, The containing folder has all folders as belonging to root even though I told it to "apply to enclosed files".

#4, Obviously, I don't want to change permissions on every single file individually.

I don't know how to change permissions to allow the folders and files to be able to be viewed by me (as a normal user) or by my SAMBA connected father. Ideas will be appreciated.

---

### Post by Dessicus on 2010-05-11
Have you tried

```
sudo chown -R yourusername /your/folder/name
```

---

### Post by ubunterooster on 2010-05-11
Well I found out what to do; finally!! ```
ubunterooster@Rooster:/media/38667506-807c-41d8-b457-7ad3b297682d$ sudo chmod -R 777 *
[sudo] password for ubunterooster: 
ubunterooster@Rooster:/media/38667506-807c-41d8-b457-7ad3b297682d$ 
```

---

### Post by ubunterooster on 2010-05-11
> **Dessicus said:**
> Have you tried

```
sudo chown -R yourusername /your/folder/name
``````

ubunterooster@Rooster:~$ sudo chown -R ubunterooster /media/38667506-807c-41d8-b457-7ad3b297682d
[sudo] password for ubunterooster: 
ubunterooster@Rooster:~$
```It's all correct now. Thanks. :D My previous post worked by allowing it all to be universally accessed which was not what I wanted, and posted before I saw your reply. Your reply _was_ what I wanted. Thanks again.

-Roo

---

