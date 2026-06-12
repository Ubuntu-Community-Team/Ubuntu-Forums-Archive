---
title: "firefox is always offline when i start it."
date: 2010-08-27
forum: General Help
---

### Post by *da-Chopper* on 2010-08-27
Hi peoples, 
I hope someone can help me here. when i upgraded my PC to 10.04, i had to add a new entry to the network interface file so it would connect to the Internet (auto etho etc.) since then firefox 3.6.3 always as being offline. each time i uncheck it then next time its offline again. is there any solution?

Thanks

---

### Post by pqwoerituytrueiwoq on 2010-08-27
that usually happens to me when my network is disabled/not connected

---

### Post by wojox on 2010-08-27
Try a new Profile [General Troubleshooting Steps]("http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html")

---

### Post by Fxy on 2010-08-27
Is there not a box under preferences somewhere that enables firefox to start in offline mode :?

...If so then you could just make sure that the box isn't ticked ;-)

---

### Post by mike555 on 2010-08-27
open Firefox and type into address bar about:config
if is the first time you are using about:config on Firefox, a warning window come in front of you, please confirm the "promise".
Then search ( type the parameter name into the "filter row" field ) for the Firefox config param named:
network.online
double click on the filtered row and set it to true
Quit and restart Firefox

---

### Post by kibbles2 on 2010-09-14
Mike555, Having the same issue.  Tried your fix to no effect.  The value was already TRUE so maybe I've gone down the wrong hole.
 
I guess I will have to do a reinstall which I am fortunately getting rather good at if I do say so myself.

---

### Post by kibbles2 on 2010-09-14
OK, I figured out what happend and have this bug fixed, I think.  When you "Hibernate" instead of "shut down" there is a bug evidently that turns off the network connections.  
 
If you right click on the odd looking networking icon, (looks like an old fishing bobber) there is a box to check that says "enable networking".  Check it and it will then allow you to operate normally.
 
I hope this helps someone else out there.  I lost a day but learned something new!

---

