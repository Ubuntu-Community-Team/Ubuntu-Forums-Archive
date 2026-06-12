---
title: "Ubuntu effects"
date: 2010-03-29
forum: General Help
---

### Post by rocket16 on 2010-03-29
Hello all. My friend installed Ubuntu 9.10 on his Desktop. He has NVidia graphics card, and got all his drivers installed, and nvidia-xgl too. But, his Visual-Effects are not working, saying that they can not be enabled. Any help?

---

### Post by chemouna on 2010-03-29
it maybe due to the problem of your Driver installation,just try to install them again (unistall then reinstall them)and then check whether your Visual Effects are working properly or no , if not its better to just reinstall ubuntu.

---

### Post by linden940 on 2010-03-29
just making sure...he HAS the most up-to-date driver for the nvidia?

---

### Post by rocket16 on 2010-03-29
Yes, he got them. But does he need to restart then?

---

### Post by rocket16 on 2010-03-29
Oh! I got the solution, it is "
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

