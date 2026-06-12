---
title: "Entering password reloads log in screen"
date: 2011-08-31
forum: General Help
---

### Post by krytorii on 2011-08-31
Every time I enter my password to log in, the screen goes black, then back to the login screen. Entering an incorrect password behaves normally. This occurs regardless of whether I select ubuntu, ubuntu classic or safe mode when logging in.

I haven't changed any important files, and the only package I've installed was imwheel, which I uninstalled before shutting down anyway. 

There is no error screen or message, I just go straight back to the login screen.

---

### Post by krytorii on 2011-08-31
Any ideas? I'm really stumped on this one. I can't think of anything I have done that would have caused anything like this.

---

### Post by krytorii on 2011-09-01
One last desperate cry for attention

---

### Post by krytorii on 2011-09-01
Sorry for multiple replies rather than editing. My phone doesn't like that edit button.

I managed to get into the terminal, and in the xsession-errors it says that it can't open /etc/X11/imwheel/startup.conf.

I had uninstalled imwheel from the software centre...


EDIT: Managed to fix it, uninstalled imwheel using ```
sudo apt-get purge imwheel
``` which removed the .conf file, then reinstalled it using ```
sudo apt-get install imwheel
``` which brought in a shiny new one.

---

