---
title: "How to remove programs auto-installed with xubuntu-desktop?"
date: 2011-01-18
forum: General Help
---

### Post by aganhuyag on 2011-01-18
I am using Ubuntu Maverick and I wanted to try the xubuntu desktop environment, so I installed xubuntu-desktop package from synaptic package manager. There were many programs automatically installed with the xubuntu-desktop.
After trying the xubuntu desktop, I didn't like it and removed it from synaptic package manager but it didn't remove the programs which were automatically installed with it.

Is there any way to remove those programs without having to remove them one by one?

---

### Post by yetiman64 on 2011-01-18
> **aganhuyag said:**
> I am using Ubuntu Maverick and I wanted to try the xubuntu desktop environment, so I installed xubuntu-desktop package from synaptic package manager. There were many programs automatically installed with the xubuntu-desktop.
After trying the xubuntu desktop, I didn't like it and removed it from synaptic package manager but it didn't remove the programs which were automatically installed with it.

Is there any way to remove those programs without having to remove them one by one?

In a terminal,

```
sudo apt-get autoremove
``` any left overs will be listed and a y/n question if you want to remove them. This should clear as you need.

---

### Post by confused57 on 2011-01-19
This might help:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by aganhuyag on 2011-01-23
Thanks for the replies!

---

