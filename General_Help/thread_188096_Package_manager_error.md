---
title: "Package manager error"
date: 2006-06-03
forum: General Help
---

### Post by drfox on 2006-06-03
I tried to install a Brother 9700 LPR package. I now have a permanent warning that tells me the package needs to be reinstalled, but apt-get can't find an archive for it. My printer is working without the LPR package, so I'd just like to delete it if possible.

Here's the output of the attempted install: oops, I can't copy and paste from the terminal error window...here's a screenshot

I've just noticed that I can no longer use Synaptic or Apt-get with this error, so it's serious

Thanks. Larry

---

### Post by bjc on 2006-06-03
Does this work?

```

sudo apt-get remove mfc9700lpr

```

---

### Post by drfox on 2006-06-03
[QUOTE=bjc]Does this work?

```

sudo apt-get remove mfc9700lpr

```[/QUOTE]

No. This is what I get:
~$ sudo apt-get remove mfc9700lpr
Reading package lists... Done
Building dependency tree... Done
E: The package mfc9700lpr needs to be reinstalled, but I can't find an archive for it.

Larry

---

### Post by blackjack6.21.91 on 2006-06-03
Post the output of

sudo apt-get install -f

---

### Post by drfox on 2006-06-04
[QUOTE=blackjack6.21.91]Post the output of

sudo apt-get install -f[/QUOTE]

sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package mfc9700lpr needs to be reinstalled, but I can't find an archive for it.

Larry

---

