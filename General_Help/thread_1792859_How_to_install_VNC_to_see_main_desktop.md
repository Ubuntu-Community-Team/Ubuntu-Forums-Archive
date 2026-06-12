---
title: "How to install VNC to see main desktop?"
date: 2011-06-28
forum: General Help
---

### Post by wrybread on 2011-06-28
I have a terminal window running from the logged in user that I'd like to monitor remotely. I installed VNC using [these instructions]("http://www.ehow.com/how_5089245_install-vnc-server-ubuntu.html"), but it shows me a different desktop than the currently logged in user. 

Is there some way to view the currently logged in user?

---

### Post by Azdour on 2011-06-29
Hi,

vnc4server will create a new vnc session which is why you are not able to see the same desktop as the logged in user, i.e. they move the mouse and your mouse does not move.

If the user is using Ubuntu then they will will need to use System | Preferences | Remote Desktop to open up their current desktop via VNC.

---

### Post by wrybread on 2011-06-29
Thank you! Works perfectly.

---

