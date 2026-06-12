---
title: "Startup Question"
date: 2009-09-19
forum: General Help
---

### Post by Don1500 on 2009-09-19
I know this has been asked before, but I can't find the answer. Every so often I know the system runs a disk check. My system does it every 3 starts. I thought it was supposed to do it every 35 or so, and I know there is a setting to change this, but I don't remember what it is. Now two questions:

[LIST=1]
[*]If the system does the check more often, is that a symptom that something is wrong?
[*]What is the config setting?
[/LIST]

---

### Post by marcopolo1981 on 2009-09-19
You can stop it from running by editing the fstab, but I wouldn't recommend doing this on a production machine.
There are various tutorials on how to edit the fstab to speed up the system within these forums, but Google should come up with a few also

---

### Post by Don1500 on 2009-09-19
Thanks

---

### Post by CatKiller on 2009-09-19
> **Don1500 said:**
> I know this has been asked before, but I can't find the answer. Every so often I know the system runs a disk check. My system does it every 3 starts. I thought it was supposed to do it every 35 or so, and I know there is a setting to change this, but I don't remember what it is.

**man tune2fs**

---

### Post by Don1500 on 2009-09-19
> **CatKiller said:**
> **man tune2fs**

Yep, Found that, thanks

I set it to 60 but I won't know if it works until it checks it again.

BUT: (From the manual for tune2fs)
"A filesystem error detected by the kernel will force an fsck on the next reboot."
I may have a problem. I'll start up on another partition and do an fsck for this one.

The way I have this set up I am checking my "/" partition and my "/home" partition at separate times. When I ran fsck on the root partition it went thru quickly and said all ok. On the /home partition it said it hadn't been checked for 26 loads. Since they are now both sync'ed they should go together, at 60 loads.

---

