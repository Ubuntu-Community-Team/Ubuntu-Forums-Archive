---
title: "Cannot access hidden (I think) directories via live cd"
date: 2009-10-30
forum: General Help
---

### Post by armageddon1 on 2009-10-30
Hi,

My ubuntu has crashed and I am trying to copy some files via a live cd (live USB). The problem is that I am not allowed to access the folder '.mozilla-thunderbird'. 

> You do not have the permissions necessary to view the contents of ".mozilla-thunderbird".

So I try to change to my old user by writing 'su myoldusername' but then it returns 'unknown id'. I guess that is because the terminal is connected to the USB while my old username only exists on a particular partition on the HD. 

Could someone please help me?

EDIT: I can access some hidden files so I guess there is a special reason why I am not allowed access to .mozilla-thunderbird or even .mozilla

Thank you.

---

### Post by girto on 2009-10-30
Open Gnome terminal in accessories and type:
gksudo nautilus

This will give you root privileges! Use carefully.

---

### Post by alphaniner on 2009-10-30
.mozilla-thunderbird usually contains all your stored e-mail, so that's probably why it has limited read permissions.  I guess .mozilla is also limited because of cache, history, etc.  Just FYI.

More importantly, girto has the right idea to solve your problem.  Just remember that the files you copy like that will be owned by root if you copy them to a Linux partition.  You will need to use **chown** to 'reclaim' them.

---

### Post by armageddon1 on 2009-10-30
Thank you! Your comments helped! :KS

---

