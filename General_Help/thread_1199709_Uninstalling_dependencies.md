---
title: "Uninstalling dependencies"
date: 2009-06-29
forum: General Help
---

### Post by chmacka on 2009-06-29
Why doesn't Synaptic uninstall dependencies?

E. g.: I want to install PiTiVi:

I find PiTiVi and mark it for installation. I hit Apply and it says: (around) **4000 kB** of extra space will be used. I hit Apply again and it Synaptic installs PiTiVi with dependencies. When I mark PiTiVi for **Complete Removal** and hit apply it says **1442 kB** of extra space will be freed.

Screenshots explain everything.

How do I remove software **and** it's dependencies? Can I do it with Synaptic? From the terminal? I know I can do it from Add/Remove Programs, but what if the program isn't listed there?

---

### Post by Legace on 2009-06-29
Type ```
sudo apt-get autoremove
``` in Terminal and it will remove useless packages ;)

---

### Post by chmacka on 2009-06-29
Thanks!

---

