---
title: "&quot;You do not have the permissions necessary to save the file&quot;"
date: 2009-07-29
forum: General Help
---

### Post by b666 on 2009-07-29
Hi, i need help. I just installed GMT (generic mapping tools), from the synaptic manager. Anyways, i need to edit a .conf file in the /etc/ directory by i get "*You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.*" Can someone please explain to me how i can easily edit that file? I just need to copy and paste a line of txt in a file. 

Bear in mind my linux skills are pathetic. Thanks.

---

### Post by CatKiller on 2009-07-29
Press Alt-F2 and run ```
gksudo gedit /name/of/file
```

You might want to read [this page]("https://help.ubuntu.com/community/RootSudo").

---

### Post by drs305 on 2009-07-29
Slower than CatKiller: Same stuff, same link.  ;-)

Open a terminal (Applications, Accessories, Terminal):
Type:
```

gksudo gedit

```
It will ask for your password. You won't see anything as you type - that's a security feature.

Edit and save the file. You opened the file as "root", so you are able to change system files and other files not owned by you.

You can read about 'root' here:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by CatKiller on 2009-07-29
> **drs305 said:**
> You won't see anything as you type

Actually, you will with *gksudo*. In a purty box and everything.

It's *sudo* (for command line programs) that doesn't print password feedback.

---

### Post by drs305 on 2009-07-29
See that's why my typing took longer than yours!  Anyone can omit stuff that doesnt' apply.  ;-)

---

