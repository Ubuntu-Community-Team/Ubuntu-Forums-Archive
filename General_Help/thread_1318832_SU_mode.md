---
title: "SU mode?"
date: 2009-11-07
forum: General Help
---

### Post by NFblaze on 2009-11-07
Hey, I think I'm having problems going into single user mode, as whenever I type *sudo telinit 1*, the init sequence runs but then it eventually gets me to either a scrambled or blank screen, and just stays exactly like that. I cant see anything, no prompt, just either the scrambled screen or blankness.  I think it might be a bug as this on occasion will happen if I do restart or shutdown, it's actually been happening since around 9.04 for my laptop if I'm not mistaken.

What is suppose to happen when I *sudo telinit 1*?

---

### Post by NFblaze on 2009-11-08
bumping it cuz I posted this late at night yesterday.

---

### Post by NFblaze on 2009-11-08
Anyone please. Take two seconds for me. Thanx.

---

### Post by benj1 on 2009-11-08
it should take you to the rescue mode menu, im not sure why it wouldnt be working for you tho,

---

### Post by NFblaze on 2009-11-08
Thanks. So must be a bug.

---

### Post by falconindy on 2009-11-08
Works fine here... Not sure why you'd ever need to do this in Ubuntu though. Does 'sudo init S' fail as well?

---

### Post by NFblaze on 2009-11-08
*sudo (tel)init S *

doesnt do anything, for my laptop. I'm not sure what it's suppose to do though, but the man page says it's suppose to take me straight to Single User mode without stopping processes. I didnt get that.

Well, I need this because was messing around to figure out a way to get ubuntu to re-detect my external hard-drive once I unplug it improperly without going thru the whole restart process,
 but now that I find out that this will always force crashing this also will allow me to report it as a bug that pops up every now and again if I do a normal shutdown/restart.

---

