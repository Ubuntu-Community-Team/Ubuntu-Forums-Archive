---
title: "Redefine terminal keys (not x-server)"
date: 2010-05-17
forum: General Help
---

### Post by baltazar3 on 2010-05-17
Im running ubuntu 9.04 remotley via ssh, using putty on a windows computer to control it. I want to redefine one key (I have a swedish keyboard where I have to press AltGr+key to get a tilde sign, would be better if I could get the tilde without AltGr modifier).

I read about xmodmap and xev. Using them I succesfully redefined the key for x-programs. For example if I start firefox over ssh and press the key I get the correct key. But in the terminal session the changes does not take effect. Which is probably logical since xmodmap does only work on the x-server. But how do I redefine the keys for terminal use?

---

### Post by gmargo on 2010-05-17
The keyboard is managed by the Windows system you're coming from.  putty/ssh is sending characters, not key up/down codes that can be mapped.

---

### Post by baltazar3 on 2010-05-17
Is there a way to remap characters?

---

