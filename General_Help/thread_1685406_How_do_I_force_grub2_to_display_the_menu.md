---
title: "How do I force grub2 to display the menu?"
date: 2011-02-10
forum: General Help
---

### Post by JRV on 2011-02-10
How do I force grub2 to display the menu on a single boot installation of Ubuntu 10.04?

---

### Post by marin123 on 2011-02-10
hold Shift when you turn on computer. when you see the menu you can let go Shift :)

---

### Post by b0b138 on 2011-02-10
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

edit /etc/default/grub

place a # at the beginning of GRUB_HIDDEN_TIMEOUT=true so its

#GRUB_HIDDEN_TIMEOUT=true

---

### Post by JRV on 2011-02-10
> **b0b138 said:**
> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

edit /etc/default/grub

place a # at the beginning of GRUB_HIDDEN_TIMEOUT=true so its

#GRUB_HIDDEN_TIMEOUT=true
Many thanks, that was easy.
Now I'll mark the thread solved.

---

