---
title: "Opening a gnome &quot;desktop&quot; session with the terminal ?"
date: 2012-02-16
forum: General Help
---

### Post by appreciation on 2012-02-16
Hello,

How can we open a gnome "desktop" session (*) with ssh ?

Thank you

(*) that is to say, a session with the same definition when the session will be started from the start screen (appearing on the screen connected to the server), containing all usernames

---

### Post by CivilizationII on 2012-02-17
> **appreciation said:**
> Hello,

How can we open a gnome "desktop" session (*) with ssh ?

Thank you

(*) that is to say, a session with the same definition when the session will be started from the start screen (appearing on the screen connected to the server), containing all usernames


Type:

> gdmflexiserver

and you're done.

Regarding the ssh stuff, you are quite probably trying to do this from a remote terminal, you then need to start an X11 session before, and attach the terminal to the X11 session.

---

