---
title: "random reboots"
date: 2011-06-24
forum: General Help
---

### Post by netopalis45 on 2011-06-24
For about the last week or so my desktop computer has been randomly rebooting itself during the night. I have a couple cron jobs, one of which runs and sometime after that it just turns off. I am running Ubuntu 10.10 on a Dell Dimension 5100 that stays on all the time as a production machine/home server. When it reboots, it never fully loads back and the screen is all messed up (sometimes looks like an old CRT did when you turned the computer off). Other times I get a scrolling list of errors (can't remember what they are right now, will edit if I see them again). All I can tell is that this is happening sometime between 7 and 8 AM. The cron jobs shouldn't be doing this, should they? Any other ideas as to why this would be happening or how I can get a log of exactly what is happening and when?

---

### Post by dino99 on 2011-06-24
many possible reasons but:

- check first your logs (often helpfull)
- check that your fans works, system not too dusty, box not under/behind tons of things (because of fresh air)
- check that cron jobs script are able to deal with errors

---

### Post by netopalis45 on 2011-06-24
Thanks for the reply. I honestly didn't even consider that it could be a hardware problem. It has been really hot here and it got kinda dusty, so I cleaned it out and hooked it back up. I will let you know if it happens again.

---

