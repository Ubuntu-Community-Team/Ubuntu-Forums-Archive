---
title: "Wait for gnome-terminal to exit"
date: 2011-06-11
forum: General Help
---

### Post by rpinsky on 2011-06-11
I have a bash script that runs a gnome-terminal. I want to wait for the user to exit the gnome-terminal before I continue on with my bash script. Unfortunitly, gnome-terminal returns control immediately.
 
My gnome-terminal runs a bash script which does an ssh to a remote node. I have tried to do a wait command on the ssh command, but the wait command falls through and doesn't wait either.
 
Any suggestions?
 
Thanks

---

### Post by TeoBigusGeekus on 2011-06-11
Ha! [Coincidence]("http://ubuntuforums.org/showthread.php?t=1780182").

---

