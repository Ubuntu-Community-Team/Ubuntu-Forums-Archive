---
title: "How to disable &quot;search hidden folders&quot;?"
date: 2009-12-27
forum: General Help
---

### Post by mak_20789 on 2009-12-27
Hi,
    I am using Hardy. I have made only one account on my laptop and have hidden some files. However I see that in "search" option, anyone using my laptop can search for hidden files. Is there any way I can disable this option?

Thank you in advance.

---

### Post by taurus on 2009-12-27
You can set permissions so no one would be able to view or read them.  Then, others wouldn't be able to access them.

```
chmod 700 directory_name
```

---

### Post by mak_20789 on 2009-12-27
> **taurus said:**
> You can set permissions so no one would be able to view or read them.  Then, others wouldn't be able to access them.

```
chmod 700 directory_name
```

Thank you for the reply.
I am sorry if I was not clear in phrasing my question.
When someone logs in to my comp, they use my user name and password. 
1) Using that password, can they change the permission to my folder and access it?
2) Besides not allowing access, I want those folders not to be visible either. Right now I do it with adding a . before the folders name, but if anyone searches for say .pdf files, then files in that hidden folder will also be listed, which I want to avoid.

Thank you in advance.

---

### Post by Vaphell on 2009-12-27
if you are the owner of the folder and people log as you, they can do whatever they want with it
Just set guest account up for others and fine tune permissions for shared stuff

---

### Post by mak_20789 on 2009-12-27
> **Vaphell said:**
> 
Just set guest account up for others and fine tune permissions for shared stuff


Dont want to do that.

---

### Post by taurus on 2009-12-27
If you want others to use your account, then there is nothing you can do to lock them out unless you change the ownership to root.  Then, even if you (log in as you) can't even access it!

p.s.  Another way is to encrypt whichever directory that you don't want others to see even if he/she logs in with your username and password.  Of course, do not use the same password (or phrase) that you're logged in with or it defeats the whole point.

---

