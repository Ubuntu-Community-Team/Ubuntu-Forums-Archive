---
title: "disable x-server at startup"
date: 2006-03-13
forum: General Help
---

### Post by Shimmy on 2006-03-13
Hello

I'm running breezy as a webserver, however, i did'nt choose the "server" installation option when installing.
So, now ubuntu is up and running with a gnome-session and a x-server which i don't need.
Now, how do i disable x-server at startup in the best way?
I do not want to uninstall x-server and gnome, just disable it.

---

### Post by Zelut on 2006-03-13
You should be able to remove the gdm package, which is the graphical login screen.  With this gone, I believe, you have to manually start X before it'll run.

..and in the future if you need to run X you can just use 'startx' at the prompt.

---

