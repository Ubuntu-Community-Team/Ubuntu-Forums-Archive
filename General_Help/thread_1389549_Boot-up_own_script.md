---
title: "Boot-up own script"
date: 2010-01-24
forum: General Help
---

### Post by bakegoodz on 2010-01-24
I am creating my own custom utility disk based on console only install of Karmic 9.10. I want it to go directly to my script with root privileges rather than run the login program (getty). I have been little familer with sys V init scripts in years past, but I'm not sure how they have changed with Upstart.

So what is a fairly simple way to have my own script autorun?

---

### Post by bakegoodz on 2010-01-31
I made a S99whatever script in /etc/rc.2/ and it ran before login

---

