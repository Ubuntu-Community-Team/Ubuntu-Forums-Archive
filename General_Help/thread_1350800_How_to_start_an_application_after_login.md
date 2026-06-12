---
title: "How to start an application after login?"
date: 2009-12-09
forum: General Help
---

### Post by weaver4 on 2009-12-09
I need to start an application after I login.  This application has a GUI and I need for it to start in my desktop.  I tried .bashrc but that only starts an app  when I start a shell.    I tried .profile but that didn't seem to work either.

Can someone tell me how to do this?

---

### Post by ubun_two on 2009-12-09
Go to Preference->Start Up Applications.  Add your app there.

---

### Post by weaver4 on 2009-12-09
I tired that and the System Monitor says it is running but the GUI for the application never shows in "my space".  I think all these items run at the root level and start before I login, so they will never show up.

In windows you just throw a link to the command in the Startup folder.

---

### Post by gadolinio on 2009-12-09
> **ubun_two said:**
> Go to Preference->Start Up Applications.  Add your app there.
+1. The same woul be to oopen a terminal and type "gnome-session-properties", then hit enter. A window will appear where you can add an application.

---

### Post by weaver4 on 2009-12-09
I'll try it again, I must be doing something wrong.

---

### Post by llamabr on 2009-12-09
Maybe it would help if we knew what you were trying to do.

---

### Post by weaver4 on 2009-12-10
I have an application that I wrote, which has a GUI associated with it.  It gives status of various equipment.

When the computer starts I need for it to do a turn-key operation of auto-logging in to a user space and starting the application automatically.

I have it kind of working now by using the suggestions above, but I would like to have a little more control over it by adding a delay before the program starts to make sure all the services have started.

When I add my application to the "Startup Applications" what file does it modify?

I also found that the .profile file gets executed upon login maybe that is a better place for me to launch a script?

---

