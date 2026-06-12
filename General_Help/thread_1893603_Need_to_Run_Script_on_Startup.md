---
title: "Need to Run Script on Startup"
date: 2011-12-10
forum: General Help
---

### Post by coolguy918 on 2011-12-10
[LEFT]I have a shell script that needs to be executed as root everytime my server is booted/rebooted. I'm sure that there's a way to do this, given how flexible Ubuntu is. Could someone point me in the right direction?
[/LEFT]

---

### Post by Lars Noodén on 2011-12-10
One way is that you can put your script in [font=Courier New]/etc/rc.local[/font].  It will get run after all the other startup scripts.

---

### Post by pqwoerituytrueiwoq on 2011-12-10
have this script run it and see if that works for you
/etc/rc.local

---

