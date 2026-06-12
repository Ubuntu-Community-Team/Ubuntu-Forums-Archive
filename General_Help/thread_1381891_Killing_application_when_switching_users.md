---
title: "Killing application when switching users?"
date: 2010-01-15
forum: General Help
---

### Post by Trapper on 2010-01-15
I have POPFile in my startup applications. I know how to automatically kill it when login out but cannot find a way to kill it if I just switch users (other than manually stopping it). It's important to kill it when using the switch users function because the new user will have access to the old user's POPFile database, have access to his email, etc, if I do not.

I have a "lynx -dump [http://127.0.0.1:8080/shutdown](http://127.0.0.1:8080/shutdown) &>/dev/null" line in my /etc/gdm/PostSession/Default file that shuts down POPFile at log out. I need to do the same or something similar when switching user. Is there a way?

---

### Post by Trapper on 2010-01-23
bump

---

### Post by dcstar on 2010-01-24
> **Trapper said:**
> I have POPFile in my startup applications. I know how to automatically kill it when login out but cannot find a way to kill it if I just switch users (other than manually stopping it). It's important to kill it when using the switch users function because the new user will have access to the old user's POPFile database, have access to his email, etc, if I do not.

I have a "lynx -dump [http://127.0.0.1:8080/shutdown](http://127.0.0.1:8080/shutdown) &>/dev/null" line in my /etc/gdm/PostSession/Default file that shuts down POPFile at log out. I need to do the same or something similar when switching user. Is there a way?

All switching users does is start and additional session, it does nothing to the existing session.

If you want something to be done then you have to create a script to do what you want and then initiate the user switch.

---

