---
title: "how can i start dfm at startup"
date: 2006-04-25
forum: General Help
---

### Post by cosmoshell on 2006-04-25
how can i start DFM Desktop File Manager at bootup if posible or when i start icewm without haveing to type it it the terminal every time i get onto my computer

---

### Post by Peter76 on 2006-05-04
Create a file startup inside /home/yourname/.icewm:

vi /home/yourname/.icewm/startup

enter the commend to run dfm ( probably dfm; don't know, I use rox...)
Save file and make executable:

chmod +x /home/yourname/.icewm/startup

restart icewm and you are done.

---

