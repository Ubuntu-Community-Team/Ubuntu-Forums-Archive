---
title: "Cannot enable Network Applet"
date: 2011-08-30
forum: General Help
---

### Post by Robkg on 2011-08-30
First: I'm a totall noob, so please explain every step simple and easy. 

I had problems with installing my WiFi, now it works if I run ```
nm-applet
``` BUT, when I close the terminal, it removes the applet and closes the connection. What should I do? How do I get the applet back permanently, I tried what was in the next quote, but I couldn't run the fist command.


> **ankur1990 said:**
> Hey Fellas
nm-applet problem solved :D :KS
Solved it own after searching long.
Method---
in the  terminal type "sudo edit /etc/NetworkManager/nm-system-settings.conf" change the "managed=false" to "managed=true" and then save it.
then in the terminal type "killall nm-system-settings"
and then reboot......
it works for me...
Try with urs and tell me the result :D:D

---

### Post by Robkg on 2011-08-30
Fixxed it myself, I disabled the Network Manager in the Start-up sequence, stupid me...

---

