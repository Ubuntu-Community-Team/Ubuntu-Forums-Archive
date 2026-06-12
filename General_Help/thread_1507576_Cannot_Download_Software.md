---
title: "Cannot Download Software"
date: 2010-06-11
forum: General Help
---

### Post by Exoskull969 on 2010-06-11
Whenever I try to download some sort of software from Ubuntu Software Center, i get a message that says 

"Requires installation of untrusted packages"
The action would require the installation of packages from not authenticated sources.


How do I fix this please?

---

### Post by ucal on 2010-06-11
System--->Administration--->Software Sources

Check the boxes that you feel are appropriate.  Universe is a good bet, and for certain issues you'll need proprietary drivers, but you don't have to check those for now.

---

### Post by Exoskull969 on 2010-06-11
I have everything on every page checked and reset to default, still have the same problem with anything I download.

---

### Post by oldos2er on 2010-06-11
> **Exoskull969 said:**
> How do I fix this please?

You need to install GPG authentication keys for any repositories you're downloading from. [https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

