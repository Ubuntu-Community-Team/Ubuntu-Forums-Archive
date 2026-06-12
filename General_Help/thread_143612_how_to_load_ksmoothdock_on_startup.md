---
title: "how to load ksmoothdock on startup?"
date: 2006-03-12
forum: General Help
---

### Post by lcbl86 on 2006-03-12
I installed ksmoothdock but I have to run it everytime I want to use it and that's always...

how can I make ksmoothdock start everytime I boot up my computer???

I'm a newbie so please explain with details...

---

### Post by Jucato on 2006-03-12
You can make a link of the ksmoothdock application in the /home/user/.kde/Autostart folder. Doesn't ksmoothdock have an option to execute on startup? Well, anyway that should do the trick. Here's a step-by-step:

1. In Konqueror, type this in the location bar: /home/[your user name]/.kde/Autostart
2. This puts you into the Autostart folder, which contains the applications that will be run once you start up KDE.
3. Right-click on an empty space and choose Create New > Link to application. A dialog box will appear.
4. In the Application tab, put ksmoothdock in the name and in the command field, type in /usr/bin/ksmoothdock (i'm presuming that's where the executable file for ksmoothdock is located). Add in other info you like. Then press OK.

That should do it. Hope this helps.

---

### Post by MetalMusicAddict on 2006-03-12
Crap. Just saw this was for Kubuntu. :)

---

