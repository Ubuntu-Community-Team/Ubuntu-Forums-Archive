---
title: "remove locked folder"
date: 2010-09-15
forum: General Help
---

### Post by tobytommy on 2010-09-15
Hello, 
How do I remove a folder that has a lock on it.  In permissions it states that root has locked the folder and I am not the owner and can not delete it.

---

### Post by CandidMan on 2010-09-15
Can I ask what folder you're trying to delete?
Anything above /home/ you need to be careful with

---

### Post by CandidMan on 2010-09-15
I'm off to catch some Zzs
You might want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=459122")

But if you absolutely have to get rid of it, try this:

Hold Alt+F2 and type
```
gksudo nautilus
```
enter your password

and hey presto, you can view and delete **any** file

'night

---

### Post by gadolinio on 2010-09-15
> **CandidMan said:**
> Can I ask what folder you're trying to delete?
Anything above /home/ you need to be careful with
+1.
Be careful when deleting something root owns.

---

