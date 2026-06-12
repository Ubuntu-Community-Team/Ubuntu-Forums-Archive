---
title: "How do I stop Update Manager from opening at startup?"
date: 2009-06-26
forum: General Help
---

### Post by Gremlinstein on 2009-06-26
Hello,
So here's my problem: I have my old dell set-up in the living room as a deddicated Boxee box running mythbuntu, and I had it set up so that when it turned on, it would launch straight into boxee. Following some updates, Update Manager now launches every time I boot up my machine, forcing me to get my laptop and VNC into the box inorder to close Update Manager so I can use boxee with my remote. 

How do I stop Update Manager from launching every time I start up my computer?

Thank you very much in advance.

---

### Post by Bucky Ball on 2009-06-26
Boot, login, close everything, click the icon to log out. Is there a box there to save settings for next time on the logout/shutdown screen? Tick it, restart.

---

### Post by mcduck on 2009-06-26
Press Alt-F2 and run 2gconf-editor" (or start it from a terminal), browse to apps/update-notifier and disable the "auto_launch"-key.

The update manager will now work like it did in previous Ubuntu versions, showing you an icon in the notification area when updates are available instead of launching the Update Manager window.

---

### Post by Gremlinstein on 2009-06-26
Thank you very much for your help. Bucky's solution worked perfectly.

---

### Post by mhh91 on 2009-06-26
there's yet another solution for this,which is disabling the update daemon from the "startup applications",you'll find it in System > Preferences

---

