---
title: "Removing compiled kernels"
date: 2006-02-06
forum: General Help
---

### Post by anandrd on 2006-02-06
I compiled a new kernel according to some instructions but it doesn't work. I just want to remove that kernel (I still have the old, working ones). How can I do this?

---

### Post by newuser111 on 2006-02-06
if you installed it as a deb, remove via synaptic or sudo dpkg -i

there may also be files related to the kernel in /usr/src

---

### Post by anandrd on 2006-02-06
No I made it from source

---

### Post by anandrd on 2006-02-06
Ok. I manually deleted the files for the new kernel and updated grub. I think that's all.

---

