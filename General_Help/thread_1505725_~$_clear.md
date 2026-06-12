---
title: "~$ clear"
date: 2010-06-09
forum: General Help
---

### Post by pwaugh on 2010-06-09
I notice when I'm in gnome-terminal and do this:

~$ clear <return>

that I can still scroll back beyond the clear.  While I can see that sometimes this might be desirable, in my case I prefer that the buffer be clear. 

Is there a way I can control this behavior?

patrick

---

### Post by Zemblan on 2010-06-09
The command ```
reset
``` will return your terminal to it's starting state, with nothing in the scroll buffer. It wont empty the command history though.

---

