---
title: "script delete"
date: 2009-08-07
forum: General Help
---

### Post by tobiasolesen on 2009-08-07
Hi 

I made a script which was suppose to initiate the starting of compiz at boot... I does not work and know I want to delete it... this I am not allowed to do... 

I did this:

gksudo gedit /usr/local/bin/start-compiz

and wrote

compiz --replace

saved and made as executable... 

know I cant erase it... I am the admin on this com

in hope for help.. 

Tobias

---

### Post by mcduck on 2009-08-07
This shouldm do the trick.
```
sudo rm /usr/local/bin/start-compiz
```

Another way is to run "gksudo nautilus" to open the file manager as root and use that to remove the file.

---

### Post by tobiasolesen on 2009-08-07
worked like a charm..

thanks...

---

