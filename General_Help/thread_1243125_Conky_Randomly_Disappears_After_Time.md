---
title: "Conky Randomly Disappears After Time"
date: 2009-08-17
forum: General Help
---

### Post by loboes41 on 2009-08-17
When I start up Conky it runs fine, but then if I leave my desk and come back sometime later, or if I'm working and then look at the desktop later, it always disappears. 

I haven't been able to time it, and as far as I can tell, its not happening because of an action I take (because often it happens when I am away).

Any ideas on how I can troubleshoot this?  A log I can check somewhere, perhaps?

I'm using Jaunty, but it also happened in both versions of Hardy.

Thanks

---

### Post by j7%&lt;RmUg on 2009-08-18
Check your conkyrc for anything that might cause this. Do you log out when your not using your computer?

---

### Post by HiImTye on 2009-08-18
try setting use_own_window to no (if it isn't set to no)

---

### Post by loboes41 on 2009-08-18
> **HiImTye said:**
> try setting use_own_window to no (if it isn't set to no)

Thanks, this seems to have fixed it.  *fingers crossed*

---

