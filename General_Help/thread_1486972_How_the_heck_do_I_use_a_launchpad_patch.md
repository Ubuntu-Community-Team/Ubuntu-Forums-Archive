---
title: "How the heck do I use a launchpad patch?"
date: 2010-05-18
forum: General Help
---

### Post by Excedio on 2010-05-18
I'm trying to implement a patch to notify-osd and I don't know how. Is there any straight forward way of doing this?
 
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508/comments/37](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508/comments/37)

---

### Post by RiceMonster on 2010-05-18
You have to download the source and the patch, apply the patch to the source with the patch utility and then recompile (given that notify-osd isn't written in python or another interpreted language).

---

### Post by Excedio on 2010-05-18
> **RiceMonster said:**
> You have to download the source and the patch, apply the patch to the source with the **patch ulity** and then recompile (given that notify-osd isn't written in python or another interpreted language).
 
Can you clarify what this is for me? I've never attempted this before.

---

### Post by RiceMonster on 2010-05-18
it's usually something like this:

```
cd src-dir
patch -p0 < /path/to/file.patch
```

---

### Post by philinux on 2010-05-18
Moved to General Help.

---

