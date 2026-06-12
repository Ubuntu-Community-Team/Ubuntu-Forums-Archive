---
title: "Opening Gui from command line."
date: 2010-03-17
forum: General Help
---

### Post by watto_one on 2010-03-17
Hi.  I'm running an upto date version of Lucid on my eeepc 901, sometimes when turning the machine on it loads to a command line sign in screen rather than the Gui screen after signing on it remains in the command line. Reason unknown. Could someone please tell me what might be wrong and what the command is to get to the Gui screen from the command line.

---

### Post by lykwydchykyn on 2010-03-17
The command would be
```

startx

```

Though if you get a console login that tends to suggest there is a problem starting the X server in the first place.

At least typing startx will give you some error output to go from.

---

### Post by Muhammad Ahmed on 2010-03-17
i had the same pblm and this solved
sudo start gdm

---

### Post by AlanR8 on 2010-03-17
Same issue with me. Occasional terminal log on screens. Picked up from another thread:

Press Alt+F7 and that takes me straight to the normal log on screen.

---

### Post by watto_one on 2010-03-17
Thanks to all. Will try all the suggestions when I get home. Will post outcomes of each.

---

### Post by watto_one on 2010-03-20
Tried all suggestions. They all worked. So again thanks

---

