---
title: "How can I make applications be delayed at startup ?"
date: 2006-06-05
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-06-05
When I boot my system and then am at the part where gnome is loading, firestarter starts first and then network manager. Then I get the error "Device not ready" and then network manager connects to my acess point and I have to start firestarter manually. Is there a way I can make network manager start earlier or make firestarter start last of the gnome applications to be loaded ?

---

### Post by caldevil on 2006-06-05
A possible workaround is a small shell script

#!/bin/sh
#wait for 30 seconds
sleep 30 
#then start your program
firestarter 

Save it as firestarter1 (or whatever name you want to give) in /usr/local/bin, make it executable.
Now in System->Preferences->Sessions->Star,Up Program, put firestarter1 instead of firestarter.

---

### Post by xXx 0wn3d xXx on 2006-06-05
Thanks that worked great.

---

