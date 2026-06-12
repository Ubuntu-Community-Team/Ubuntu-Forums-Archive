---
title: "Change system time from 12h to 24h"
date: 2009-10-31
forum: General Help
---

### Post by Aero-Z on 2009-10-31
Hello,

I'm wondering how can I change the whole system time format from 12h to 24h. My regional settings are set but programs still show time as AM/PM. Programs like Gajim and Emesene for example.

Thanks

---

### Post by Aero-Z on 2009-11-02
bump

---

### Post by Giblet5 on 2009-11-02
System time is not tied to 12/24 except on very old VCRs and microwave ovens.

Each application chooses how it will display time - just like on every other OS.

You can change a specific application's time representation on a system-wide basis (ie, all users) only if that application provides an option to do so either via a command-line option, or an X resource (see Xorg man page, or Volume 3 of "The X Window System" by O'Reilly & Assoc.)

Now, if you're only trying to change it for YOUR user account, then you can try adding an X resource to try and catch any application that interprets the "twentyfour" X resource by adding "*.twentyfour: true".

See the man pages: ```
man X ## Overview of Xorg
man appres ## View an application's resources and current defaults
man xrdb ## resource manipulation
```


And you thought there was a checkbox somewhere...  ;)

---

### Post by Uncle Spellbinder on 2009-11-02
> **Giblet5 said:**
> ...And you thought there was a checkbox somewhere...  ;)

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/Time.jpg[/IMG]

---

### Post by Aero-Z on 2009-11-03
> **Uncle Spellbinder said:**
> [IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/Time.jpg[/IMG]
Not talking about clock applet.

---

### Post by Aero-Z on 2009-11-04
bump. Looking for some easier solution than Giblet5's

---

