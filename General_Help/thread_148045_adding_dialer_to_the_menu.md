---
title: "adding dialer to the menu?"
date: 2006-03-21
forum: General Help
---

### Post by s_spiff on 2006-03-21
I have a dialer to my broadband, which is a java based application. called BroadbandUI.jar
 located : /home/user-name/Desktop/Connection

everytime I want to make a connection I need to go to that file...right click on it, say open with java..then enter my username and password etc. Is there a way add it to the menu [ Applications ] such that the no. of clicks required to start the damn thing is reduced? or someway to get it to start on boot up. I know i can edit the startu up programs list, but i can't figure how to add it there such that it opens the .jar in java. Any ideas?

---

### Post by varunus on 2006-03-21
Try right clicking the applications menu and choosing edit menus.  Can you make a new entry for the dialer, with the command "java /path/to/BroadbandUI.jar"?  If this works, can you add that to your startup session?

---

### Post by s_spiff on 2006-03-21
well that didn't work... anything else?
I added it so:
java /home/alok/Desktop/Connection/BroadbandUI.jar

---

