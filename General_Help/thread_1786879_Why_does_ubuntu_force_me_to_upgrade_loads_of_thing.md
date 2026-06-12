---
title: "Why does ubuntu force me to upgrade loads of things, when I only want to upgrade one?"
date: 2011-06-20
forum: General Help
---

### Post by newtyron on 2011-06-20
Hi,

I use joomla and it only works with php5.2

I keep having to downgrade because ubuntu tried to upgrade to php5.3 everytime I try to upgrade something.

For instance, I just upgraded wine and didnt notice php5.3 in there as a dependancy, so now have to downgrade AGAIN!

Is there a way to upgrade wine without upgrading php as well?

Cheers

N

---

### Post by Matt__ on 2011-06-20
open synaptic, type in the package/program name, select it and from the 'package' drop down menu 'lock version'.

---

### Post by ajgreeny on 2011-06-20
> **Matt__ said:**
> open synaptic, type in the package/program name, select it and from the 'package' drop down menu 'lock version'.
That only does it for synaptic and update manager as far as I'm aware.

You can pin a package system wide with an addition of three lines to the /etc/apt/preferences file
```
Package: *name*                
Pin: version *current number from repos*
Pin-Priority: 1001
```

---

