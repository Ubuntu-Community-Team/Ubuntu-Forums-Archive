---
title: "best place to put startup scripts?"
date: 2009-09-17
forum: General Help
---

### Post by sa125 on 2009-09-17
Hi - 
I have a couple of shell scripts I'd like to run after each startup. Where's the best place to put them? Inside ~/.profile?

Thanks!

---

### Post by jimjawn on 2009-09-17
Any script that you place in /etc/rc.local will be run each time the server starts for each users.  You can read the text in the file for some more info.

---

### Post by sa125 on 2009-09-21
cool, thanks!

---

