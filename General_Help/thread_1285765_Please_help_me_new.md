---
title: "Please help me *new*"
date: 2009-10-08
forum: General Help
---

### Post by An-na on 2009-10-08
Hi everybody,

I am a new Ubuntu user (8.04 LTS) en I just started the Update Manager. Unfortunately my computer crashed in the middle of the update. Now I can't update Ubuntu again. 
I get the following message when I open the Update Manager:

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

Who knows what to do?

---

### Post by Peter09 on 2009-10-08
The answer is in the error message, open a terminal (from the applications->accesories menu) and type the following followed by enter

```
sudo *dpkg --configure -a*
```

---

### Post by pmlxuser on 2009-10-08
open the command prompt 
and type the folloeing```
$ sudo dpkg --configure -a 
```

---

### Post by An-na on 2009-10-08
Thank you both...! :)

But it's not working, because the terminal won't open...

---

### Post by mechro on 2009-10-08
Alt F2 from the Desktop will get you a quick "run application" box.

Enter *gnome-terminal* and you may get a Terminal.

---

### Post by bumanie on 2009-10-08
You can boot into recovery mode and try > sudo dpkg --configure -a

---

