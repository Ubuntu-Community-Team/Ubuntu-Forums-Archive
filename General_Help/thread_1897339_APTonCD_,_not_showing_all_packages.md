---
title: "APTonCD , not showing all packages"
date: 2011-12-19
forum: General Help
---

### Post by maruf10 on 2011-12-19
Hi
I am trying to create APTonCD . But It's not showing all my installed package list . From where can I found all package list so that I can add them to APTonCD ??

I am using ubuntu 11.04
Thanks in advance.

Maruf

---

### Post by kanishkdudeja on 2011-12-19
Only the packages you installed yourself manually, will be shown in aptoncd. 

And that too only if you have'nt run this command:

```
sudo apt-get clean
```

If you have run this command, then the contents of /var/cache/apt/archives/ directory (which contains the deb files of the packages you installed manually) will be emptied.

And therefore aptoncd will show no packages.

---

### Post by maruf10 on 2011-12-19
so what should I do now to get all package list ??

---

### Post by kanishkdudeja on 2011-12-19
If you have run the command, then there is no way you can recover those packages.

They have been permanently deleted, but only if you have run the command.

---

