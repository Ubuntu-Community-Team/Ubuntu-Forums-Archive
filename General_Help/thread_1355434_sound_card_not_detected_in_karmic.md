---
title: "sound card not detected in karmic"
date: 2009-12-14
forum: General Help
---

### Post by muse3332 on 2009-12-14
basicly i put in a command that someone gave me and it says no soundcards found.. please dont give me a link to another post please.. i want to fix this already isnt it right for evryone using ubuntu to be able to see hear and enjoy?

---

### Post by gordintoronto on 2009-12-15
You're right, sound is an essential!

What sound card is in your computer?  If it's on the motherboard or in a slot, the Terminal command lspci should show it.

Can you run Preferences/Sound and see if there is anything in the Input and Output tabs?

---

### Post by muse3332 on 2009-12-15
hi thank you for your reply it means a lot! ok it says my sound card is not detected! D:

---

### Post by gordintoronto on 2009-12-16
What sound card do you have?  How about lspci?

---

### Post by DaVince21 on 2009-12-16
> please dont give me a link to another post please..
What if that other post provided a good solution? It only makes sense to link you then...

Anyway, yeah. We need hardware information. Run this in a terminal and copy-paste its output here:
```
lshw -c sound
```
(Or run lspci as suggested, which does the same but shows more compact information. :P)

---

