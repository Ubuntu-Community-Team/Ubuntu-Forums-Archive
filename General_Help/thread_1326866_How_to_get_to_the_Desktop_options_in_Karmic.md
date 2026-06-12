---
title: "How to get to the Desktop options in Karmic?"
date: 2009-11-14
forum: General Help
---

### Post by Pott on 2009-11-14
In XFCE on 9.04, you can select for instance which icons you want to keep on the desktop and which would go away... 

Is this at all possible for Karmic/Gnome? I want a clean desktop. So I need to get the mounted drives out of the desktop, and only allow Downloads there. It'll allow my Conky to be better setup too. 
Thanks!

---

### Post by 73ckn797 on 2009-11-14
Install Ubuntu Tweak and you can do many things, including what you ask.

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by listerofsmeg1 on 2009-11-14
Alt+f2 > gconf-editor
apps > nautilus > desktop and uncheck volumes_visible and any other *_visibles will clear it.

---

### Post by Pott on 2009-11-14
Excellent thank you :)

I did have Ubuntu Tweaks installed. BUT... I had on it some of the same options available through the System options. For instance, I have some extra Startup scripts/launchers that are in System, but weren't present in Ubuntu Tweaks. So I wasn't sure which would get priority etc... so I just uninstalled it.

---

### Post by 73ckn797 on 2009-11-14
> **listerofsmeg1 said:**
> Alt+f2 > gconf-editor
apps > nautilus > desktop and uncheck volumes_visible and any other *_visibles will clear it.

Another way is to open System/Preferences/Main Menu. Under System Tools enable "configuration editor". It will show up under Applications/System Tools. You can then follow the "apps > nautilus > desktop and uncheck volumes_visible and any other *_visibles will clear it." recommendations. The GUI will allow future "tweaking" also.

---

