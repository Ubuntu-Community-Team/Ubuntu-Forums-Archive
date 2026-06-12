---
title: "Howto put display to sleep manually?"
date: 2006-04-14
forum: General Help
---

### Post by SirKillalot on 2006-04-14
Is there a program which can put my display to sleep if I want it to?

---

### Post by 5-HT on 2006-04-14
```
 xset dpms force OPTION 
``` ; where OPTION takes the form of one of {'standby', 'suspend', 'off', 'on'}

For more information, see 'man xset'.

Hope that helps.

---

### Post by tajmox on 2006-10-20
That's great!
Now how do I make it so that when there is x minutes of inactivity, that command launches?

Ubuntu's power management doesn't work for me..

---

