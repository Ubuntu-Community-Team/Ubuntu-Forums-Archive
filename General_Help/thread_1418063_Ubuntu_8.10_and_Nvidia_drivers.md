---
title: "Ubuntu 8.10 and Nvidia drivers"
date: 2010-02-28
forum: General Help
---

### Post by GSI on 2010-02-28
I'm trying to enable the Nvidia drivers so I can use the Desktop effects and play games but when I go to Systen -->Administration-->Hardware drivers It say that There are no proprietary drivers in use.Can anybody help me install the Nvidia driver?

---

### Post by 3rdalbum on 2010-02-28
You need to reload the package list. First, go to System > Administration > Software Sources and make sure that the first four checkboxes are ticked. Close Software Sources. Now go to System > Administration > Synaptic Package Manager and click the Reload button.

When that's finished, close Synaptic and open Hardware Drivers and it should be good to go.

I should also mention that you need an internet connection.

---

### Post by GSI on 2010-03-01
Yes,thank you It worked :)

---

