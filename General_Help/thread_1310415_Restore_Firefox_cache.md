---
title: "Restore Firefox cache"
date: 2009-11-01
forum: General Help
---

### Post by mthalis on 2009-11-01
I going to install Ubuntu 9.10, but I want to restore my previous(Ubuntu 9.04) web browsing history and add them new Firefox(9.10 Firefox). How can i do this?

---

### Post by winotree on 2009-11-01
1. Back-up or copy your /home/user/.mozilla file **or** even better 
2. Back-up or copy your /home/user file 

and use it to restore your files and configurations.  You could use **grsync** from the repositories [Synaptic Package Manager] or simply copy and paste.

---

### Post by mthalis on 2009-11-01
Thanks for reply, if you can provide more details( reference link) regard this that is very helpful to me(I want restore only my Firefox cache- website)

---

### Post by winotree on 2009-11-01
I don't know how long it would take me to find you a reference link to verify -- this is just something I do.  :)  If all you want is your viewing history then I think you'd save

/home/user/.mozilla/firefox/<random.default>/Cache

although I don't even use that anymore, having moved my cache to /tmp to gain a bit of speed on this small device, then deleting it each night.  So the only thing I have to guide you with is my memory.  ;)

---

