---
title: "Lost Sound"
date: 2012-07-26
forum: General Help
---

### Post by borgward on 2012-07-26
The sound quit working with Ubuntu 10.04 on my Dell Inspiron 1520 laptop. Booted Knopix, get sound there.

Kept getting notice that sound was not working when I opened applications, even though sound was not involved w/them, and sound was still working w.Rhythembox.

No sound today. What command do I use to read recent error messages.

---

### Post by mastablasta on 2012-07-26
what sound card do you have?
 
you could try
sudo alsa reload -c
 
this should reload sound modules.
see if it helps.

---

### Post by borgward on 2012-07-26
Thanks, that worked.

---

