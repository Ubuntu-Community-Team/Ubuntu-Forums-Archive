---
title: "What does &quot;Instead, install the linux-generic meta-package&quot; mean?"
date: 2010-03-04
forum: General Help
---

### Post by cforput on 2010-03-04
Update manager popped up today and I actually had some time to look through the updates. In the recommended updates section it lists "linus-image-2.6.31-20-generic (New install)."

In the description is says "You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

I have read 2 different threads that talk a little about this message but I am still unclear on what it is trying to tell me. What does it mean when it says to "Instead, install the linux-generic meta-package"

---

### Post by solitaire on 2010-03-04
The "meta-package" is basically a link to the latest version of a package (including all dependencies)
usually used when you want to install a group of programs which are interdependent on each other

---

### Post by michy99 on 2010-03-04
The linux-generic meta-package is already installed by default. It takes care of updating to new kernel versions. That is why the new kenel is appearing in the updates. The message basically warns against installing the kernal manually with Synaptic or apt-get, for example.

---

### Post by cforput on 2010-03-04
michy99,
thank you for your explanation. Your's made the most sense and I now understand why the description says what it does. I will mark this as solved.

---

