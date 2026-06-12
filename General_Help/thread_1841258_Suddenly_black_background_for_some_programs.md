---
title: "Suddenly black background for some programs"
date: 2011-09-09
forum: General Help
---

### Post by Arndt on 2011-09-09
Yesterday I noticed that two programs have started to behave differently from before: xterm and Emacs 22. Both used to start with a white background and black text, now they start with black background and light text. In addition, emacs has a smaller font than usual.

This may have happpened when I experimented with a ~/.fonts.conf file. I don't usually have one, and I saw a suggestion on a forum on how to turn off antialiasing. Later I removed that file again.

What can have happened, and where are settings like this kept? I don't know what will happen if I reboot - I'd like to be able to fix this without rebooting.

Most other programs (for example gnome-terminal) are not affected.

I use Lucid (10.04).

---

### Post by Bodsda on 2011-09-09
> **Arndt said:**
> Yesterday I noticed that two programs have started to behave differently from before: xterm and Emacs 22. Both used to start with a white background and black text, now they start with black background and light text. In addition, emacs has a smaller font than usual.
 
This may have happpened when I experimented with a ~/.fonts.conf file. I don't usually have one, and I saw a suggestion on a forum on how to turn off antialiasing. Later I removed that file again.
 
What can have happened, and where are settings like this kept? I don't know what will happen if I reboot - I'd like to be able to fix this without rebooting.
 
Most other programs (for example gnome-terminal) are not affected.
 
I use Lucid (10.04).
 
You say that Emacs has the problem but not gnome-terminal. Is Emacs running a GUI instead of from the terminal?
 
That fonts.config file is a user specific file so if you removed it any apps that reference your user specific fonts.conf file might fall back to application defaults. They should really look at the global file in /etc/fonts/fonts.conf
 
Can you try copying that file to your home folder
```

sudo cp -v /etc/fonts/fonts.conf ~/fonts.conf && chmod 755 ~/fonts.conf

```
 
Thanks,
Bodsda

---

