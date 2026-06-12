---
title: "Ubuntu software center doesn't work"
date: 2010-02-24
forum: General Help
---

### Post by anur.bhargav on 2010-02-24
Hi Everybody,:(

Of late i'm not able to install or uninstall any program from the ubuntu software center...
The install and remove buttons appear ,but when i click them there's no response
Please help!!
Thanks in advance:)

---

### Post by argail1980 on 2010-02-24
open a terminal (Applications > Accessiores > Terminal) and type

```
sudo apt-get install synaptic
```

synaptic is another (imho better) software maganer than the software center. If this command gives you errors, other than smth. like "already installed", post them here, please.

If it installs properly, open synaptic via (System > Administration > Synaptic) and install the software you want from there.

---

### Post by anur.bhargav on 2010-02-24
> **argail1980 said:**
> open a terminal (Applications > Accessiores > Terminal) and type

```
sudo apt-get install synaptic
```

synaptic is another (imho better) software maganer than the software center. If this command gives you errors, other than smth. like "already installed", post them here, please.

If it installs properly, open synaptic via (System > Administration > Synaptic) and install the software you want from there.
Wow great that worked...I had no errors..
Thank u.. but is there any way to get ubuntu software center back to working condition :)

---

### Post by argail1980 on 2010-02-24
Try marking it for reinstall in synaptic. If u don't get any error messages from the software center, it's quite hard to figure out why it does not work any more.

---

### Post by anur.bhargav on 2010-02-24
> **argail1980 said:**
> open a terminal (Applications > Accessiores > Terminal) and type

```
sudo apt-get install synaptic
```

synaptic is another (imho better) software maganer than the software center. If this command gives you errors, other than smth. like "already installed", post them here, please.

If it installs properly, open synaptic via (System > Administration > Synaptic) and install the software you want from there.
[SIZE="4"]THANK U!!![/SIZE] that helped..its just like the ubuntu software centre..in fact even better:popcorn::KS

---

### Post by raghugonzalez on 2010-02-24
Does the synaptic manager work?
If so try to fix all broken packages. Then try the ubuntu software center. If there is a lock on the database it does not allow installing new apps. Thata when reading the repositories


I don't know if this solution works. I hope this info help.

Regards,
Raghu> **anur.bhargav said:**
> Hi Everybody,:(

Of late i'm not able to install or uninstall any program from the ubuntu software center...
The install and remove buttons appear ,but when i click them there's no response
Please help!!
Thanks in advance:)

---

### Post by gabak on 2011-06-26
try this

[http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center](http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center)

---

