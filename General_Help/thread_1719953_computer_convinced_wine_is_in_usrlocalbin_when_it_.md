---
title: "computer convinced wine is in /usr/local/bin when it is in /usr/bin"
date: 2011-04-02
forum: General Help
---

### Post by Zorgoth on 2011-04-02
If I try to say 'wine *.exe' I get "bash: /usr/local/bin/wine: No such file or directory"

Wine works fine if I say /usr/bin/wine *.exe.

How do I make it so wine means /usr/bin/wine?

---

### Post by gmargo on 2011-04-02
Do you have more than one wine installed?  Or perhaps an alias?  At the bash command prompt, type:
```

type -a wine

```to find out all the places wine is defined.  The first line is the one usually executed.

---

### Post by Zorgoth on 2011-04-02
I get

wine is /usr/bin/wine

but it still expects it to be in /usr/bin/local/wine for some reason.

This happened after I compiled wine 1.3.17 and then I uninstalled it (with sudo make uninstall) and replaced it with the debian package of wine 1.3.15 in the repository.

---

### Post by gmargo on 2011-04-02
Perhaps you just need to do a "hash -r" to make bash forget it's internal hashed location list.  Or start a new shell.

---

### Post by Zorgoth on 2011-04-03
hash -r did the trick!  Thanks!

---

