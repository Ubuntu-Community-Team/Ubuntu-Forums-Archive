---
title: "The panel encountered a problem while loading..."
date: 2009-09-10
forum: General Help
---

### Post by ant2ne on 2009-09-10
I get a bunch of errors on login saying
> The panel encountered a problem while loading
and then > 
OAFIID:GNOME_MixerApplet
Do you want to delete the applet from your configuration Then one for fast user switcher applet etc. I'd say about 10-15 of them. This error just recently begin.

---

### Post by shane2peru on 2009-09-10
> **ant2ne said:**
> I get a bunch of errors on login saying

and then  Then one for fast user switcher applet etc. I'd say about 10-15 of them. This error just recently begin.

Somehow this app, gnome-panel-data got removed, you need to install it again.  Then after it is installedhit alt-f2, and type, ```
 killall gnome-panel
```  That will reload your panel and everything should be back, with no errors.

Shane

---

