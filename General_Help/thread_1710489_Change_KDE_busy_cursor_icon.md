---
title: "Change KDE busy cursor icon"
date: 2011-03-19
forum: General Help
---

### Post by decktrio on 2011-03-19
I downloaded Angry Birds for windows, and it runs perfectly through wine. Then, I wanted to add a link with an angry birds icon to my Desktop... so I made a simple bash script to run Angry Birds, and saved it to my bin. Using "link to application" (when I right click on the Desktop and go to "Create New"), I placed an Angry Birds icon on my desktop.

Obviously it all works fine, but when I click on the icon, KDE's busy cursor doesn't "bounce" the Angry Birds icon. Instead, the general applications icon (the gear) bounces. How can I change the busy cursor icon so that it's unique for a specific application?

Thanks, in advance.

---

### Post by Zorael on 2011-03-21
Right click the script launcher, hit Properties and then click the current icon (next to the launcher name) to open up the icon selection menu. Once the launcher has an icon, the bouncing busy notification should inherit it.

---

### Post by decktrio on 2011-03-21
:) First off, thanks for the reply.

I had done that already. [I knew my explanation wasn't clear! smh] So, the icon's been changed on the desktop, but when I launch the app, my busy cursor "bounces" the applications icon (the "gear"), as opposed to bouncing the new icon on the desktop.

---

### Post by Zorael on 2011-03-21
What version of KDE are you running? I tried it before replying and it works for me...

With a vanilla launcher I get the gear, but if I change it the bouncing icon changes too. The launcher .desktop file points to a script in my bin that does nothing.

Slightly redacted;
```
[Desktop Entry]
Exec=/home/zorael/bin/naninuneno
**Icon=bball**
Name[en_GB]=Link to Application
Name=Link to Application
Path=
StartupNotify=true
Terminal=true
Type=Application
```

---

### Post by decktrio on 2011-03-21
> **Zorael said:**
> What version of KDE are you running?

I'm using KDE 4.5.3

---

### Post by Zorael on 2011-03-21
Then I'm not sure. It may well be a bug that's fixed in 4.6.

---

### Post by decktrio on 2011-03-23
Oh, well. It's not a big deal the apps work fine, it was just a matter of appearance/details. Thanks for all the help, though! :D

---

