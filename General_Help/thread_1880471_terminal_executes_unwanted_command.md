---
title: "terminal executes unwanted command"
date: 2011-11-13
forum: General Help
---

### Post by DevinJCan on 2011-11-13
Hello and thanks for stopping in on my thread

Every time I open a terminal I get this:
> bash: export: `/home/djc/android-sdk-linux': not a valid identifier
djc@djc-M480:~$ 


I am wondering why this is happening and how to change it.

---

### Post by Habeouscorpus on 2011-11-13
Aha. If you would be so kind, please type this in your terminal.

```
 gedit ~/.bashrc 
```and paste what's in the resulting gedit window. 

When your terminal opens, it looks through the file above, .bash.rc. If it finds an error, it complains, retunring something like what you got. It looks like something tried to set an environment variable (which you do by editing .bash.rc) and messed up the syntax, so bash is complaining. I can confirm this when you paste.

---

