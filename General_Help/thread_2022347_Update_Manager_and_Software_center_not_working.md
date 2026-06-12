---
title: "Update Manager and Software center not working"
date: 2012-07-10
forum: General Help
---

### Post by dfwlucas on 2012-07-10
Hello Ubuntu forums i have a big problem that i need help with
so earlier today I was trying to install openfoam but gave up but now when i try to open Update manager It has an error saying E:Malformed line 1 in source list /etc/apt/sources.list.d/openfoam.list (dist parse) PLEASE HELP QUICKLY D:

---

### Post by CLCressman on 2012-07-10
Do you have Synaptic installed?

---

### Post by claracc on 2012-07-11
Post your /etc/apt/sources.list file, probably in the first line of the file there is a wrong character or something similar.

---

### Post by dino99 on 2012-07-11
sudo rm /etc/apt/sources.list.d/openfoam.list

---

