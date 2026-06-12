---
title: "Access rights"
date: 2009-08-06
forum: General Help
---

### Post by i-like-knives on 2009-08-06
I cannot edit documents in Open Office. It says I do not have the access rights.
Just clean installed 8.04
I also don't remember changing root permissions, could this be the issue?
I have spent some time now reading and am not getting the answers I need.
Would someone help with OO prob and also tell me how to check and change root permissions? Thanks much.
(prob need the code written for me, still learning here)

---

### Post by burmanabhay88 on 2009-08-06
> **i-like-knives said:**
> I cannot edit documents in Open Office. It says I do not have the access rights.
Just clean installed 8.04
I also don't remember changing root permissions, could this be the issue?
I have spent some time now reading and am not getting the answers I need.
Would someone help with OO prob and also tell me how to check and change root permissions? Thanks much.
(prob need the code written for me, still learning here)

easy solution: goto your terminal, goto the folder where in you've kept your file. change the permission on the file using

> chmod 777 (filename)

you'll have all necessary permissions.

tell me if it helps. or any probs u face.

---

### Post by Pythack on 2009-08-06
Hello.

Try run openoffice in root (although it is inadvisable).

Otherwise. Change file's chmod with:

```

sudo chmod 777 filename.odp 

```

Pythack.

---

