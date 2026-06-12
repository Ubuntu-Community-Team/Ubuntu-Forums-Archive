---
title: "How to uninstall Shiretoko Web Browser?"
date: 2009-09-24
forum: General Help
---

### Post by zking on 2009-09-24
I recently installed the Shiretoko Web Browser (a.k.a Firefox 3.5) 

I still have Firefox 3.0.14 installed, and I kind of like it better than Shiretoko. 

How do I uninstall Shiretoko?

---

### Post by Vaphell on 2009-09-24
launch synaptic and look for firefox-3.5, mark for removal, apply - voila

---

### Post by lovinglinux on 2009-09-25
Shiretoko is installed side-by-side and launched via a separate launcher "Applications >> Internet >> Shiretoko Web Browser". So unless you have manually changed the Firefox launcher to point to Shiretoko or installed FF 3.5 using a different method, you will still be able to launch FF 3.0 using it's own launcher.

Which method did you use to install Firefox 3.5?

If you installed it from the repositories then run this command to remove it:

```
sudo apt-get remove firefox-3.5
```

Keep in mind that Shiretoko uses a different profile folder, which is ** ~/.mozilla/firefox-3.5** while Firefox 3.0 uses **~/.mozilla/firefox**. So if you decide to remove Shiretoko, you might need to copy your profile folder from **~/.mozilla/firefox-3.5** to **~/.mozilla/firefox** in order to keep settings and bookmarks changed while using Shiretoko.

Anyway, why don't you like Shiretoko? It's much faster than FF 3.0.

You might want to read my tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

