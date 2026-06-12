---
title: "launch a .sh script from docky"
date: 2011-07-21
forum: General Help
---

### Post by titane on 2011-07-21
Hi, I just created a simple shell script, it works well, but when I try to run it from Docky it launches Gedit :-/

Is there a way I can run the script instead?

---

### Post by TeoBigusGeekus on 2011-07-21
Have you made the script executable?
```
chmod +x /path/scriptname
```

---

### Post by titane on 2011-07-22
yep, I can run it from nautilus.
with nautilus I can "run in a terminal", "display", "cancel" or "run".
but Docky don't ask and display it.

---

### Post by holloway on 2011-07-24
> **titane said:**
> yep, I can run it from nautilus.
with nautilus I can "run in a terminal", "display", "cancel" or "run".
but Docky don't ask and display it.

Drag the script to your Gnome toolbar to make a launcher, and then drag that launcher to Docky.

---

### Post by thewanderorux on 2012-11-17
> **holloway said:**
> Drag the script to your Gnome toolbar to make a launcher, and then drag that launcher to Docky.

Thanks holloway, that was the solution I was looking for!

After upgrading from 10.10 to 12.04 I have lost my gnome panel applet file-browser-applet which provided a very quick access to my scripts folder and it was very light, cool and fast. I was able to start my scripts (synergy-restarter, backup, screenshot, vpnstarter, ...) with 2 clicks. It was like a panel drawer but automatically updated from the file system. 

Sadly the panel applet is no more available, so I created another docky panel to add the scripts. They were opened in the default text editor. 

Now with your tip it's working for me. It seems that gnome-panel automatically creates a desktop launcher for the script. Now I can run and execute the script from docky directly. Thanks, man!

---

