---
title: "deluge webui not writing changes"
date: 2010-09-09
forum: General Help
---

### Post by doralsoral on 2010-09-09
Ive got a dedicated server setup to run the deluge daemon and access it through thee webui. i can add and even delete new torrents just fine but when i go into the options and try to change values like upload speed limits etc the changes dont take. im assuming this is a permissions issue but i don't know what files or directories to change.

---

### Post by Origin_Unknown on 2010-09-13
i had this issue until I downloaded 'deluged' via the software centre and then in deluge un-tick 'classic mode enable' under the interface tab in settings. 
When you then access the web ui, the button on the top right should be connection manager, you can then point it at the right IP of the machine with deluge installed, the right port for the daemon and the username and password 

hopefully this should work (its pretty much what i did - while i cant remember correctly as I'm at work)

---

