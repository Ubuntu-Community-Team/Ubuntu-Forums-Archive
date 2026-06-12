---
title: "Help get my Terminal Server Client running :)"
date: 2010-01-23
forum: General Help
---

### Post by pawnrocket on 2010-01-23
I am building a Terminal Server Client using debootstrap for work. I found a couple post that suggested that I can change my inittab configuration to not load login. However it is my understanding that inittab has been replaced by upstart. 

I would like to know how to modify upstart so that instead of the user seeing a login: prompt my script is automatically loaded (rrdesktop)(revisedrdesktop) and the user is brought off a live cd to my terminal server. 

Using Karmic and lots of old hardware

any ideas?

---

### Post by pawnrocket on 2010-01-23
or can I just add an rc.local to /etc/skel ?

---

### Post by pawnrocket on 2010-01-23
nevermind 

/etc/init/rc-sysinit.conf

# rc-sysinit - System V initialisation compatibility
#
# This task runs the old System V-style system initialisation scripts,
# and enters the default runlevel when finished.

---

