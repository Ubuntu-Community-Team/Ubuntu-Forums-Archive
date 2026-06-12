---
title: "Rolling back from AWN"
date: 2009-12-22
forum: General Help
---

### Post by hotshot247 on 2009-12-22
i started using avant window navigator for a while but i want to go back to my old panels just for a change. i know how to add the panels on the top and bottom but how do i set the panels to where they are exactly like ubuntu was when i first installed it? thanks in advance for your help!

---

### Post by cake nom nom on 2009-12-22
You mean with the icons and stuff?

---

### Post by howefield on 2009-12-22
> **hotshot247 said:**
> ..how do i set the panels to where they are exactly like ubuntu was when i first installed it?

Try opening a terminal and typing the following.

```
rm -r ~/.gconf/apps/panel
```

This will remove the current configuration and be rebuilt when you log out and back in.

You don't have to remove the folder, if you prefer you could rename or simply move it, so that you can put it back if it doesn't go to plan :P

---

### Post by hotshot247 on 2009-12-22
> **howefield said:**
> Try opening a terminal and typing the following.

```
rm -r ~/.gconf/apps/panel
```This will remove the current configuration and be rebuilt when you log out and back in.

You don't have to remove the folder, if you prefer you could rename or simply move it, so that you can put it back if it doesn't go to plan :P

thanks for your help!! i just tried it and it works.

---

### Post by howefield on 2009-12-22
> **hotshot247 said:**
> thanks for your help!! i just tried it and it works.

I'd a feeling it might.... 
:lolflag:

---

