---
title: "is it safe to uninstall HAL in ubuntu 10.04 and 9.10?"
date: 2010-03-04
forum: General Help
---

### Post by cgb223 on 2010-03-04
at this point in time in the alpha world of lucid, can I uninstall HAL from Ubuntu 10.04? i tried it on 9.10 2 weeks ago and unfortunately the dependencies also uninstalled the entire gnome desktop and many other essential things leaving me with a bulky half broken mock arch linux. if this is safe let me know I am dying to try out Device Kit to see how fast it really is. (Ive heard its much faster than what HAL would allow)

---

### Post by baser5nature on 2010-03-05
I just (as in a few minutes ago) selected complete removal in synaptic of hal and all is well.  have only rebooted once since.  I didn't time it but it seemed to take longer to get to the ubunut splash, but the splash only lasted a couple seconds.  I'm going to remove the hal-info package now to see what happens.

edit: i'm using 10.04 alpha 2, upgraded from 9.10 fresh install.

---

### Post by cgb223 on 2010-03-05
just a follow up. removed Hal (not sure about hal-info) the computer is faster, the device kit packages are installed already. it works, the problem i had seemed to be with the old list of dependencies. now I'm not sure if this is related but now my left click function is reversed with my ctrl-left click, each one doing the other. this only happens in gnome, (i have kde installed too, it works fine there). do you think this could be related?

---

### Post by baser5nature on 2010-03-07
i was also able to completely remove hal-info. libhal1 and libhal-storage1 cannot be removed without what looks like the rest of gnome...

---

