---
title: "Preferred applications"
date: 2010-10-12
forum: General Help
---

### Post by reobedr on 2010-10-12
After my upgrade to Ubuntu 10.10, there are two "preferred applications" shortcuts in the System/preference menu. One points to: "gnome-default-applications-properties" and the other to: "/usr/bin/libfm-pref-apps"

When I start the first I can set the preferred apps for internet, multimedia, system and Accessibility.(same as lucid) With the second I can only set the browser and email app, however, the settings are not saved.

Also when I click an URL in an email nothing happens, which suggests that there is no default application set up.

I tried reinstalling the libfm-gtk0 package, but to no avail.

Anyone knows how to solve this?

---

### Post by reobedr on 2010-10-13
Some more info I found out:

Adding:
```
 user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```
 to the prefs.js in th profile folder did not help.

Also clicking a mailto: in firefox, does work...

Now I'm truly puzzeled...

---

### Post by kerry_s on 2010-10-13
sounds like you got some xfce mixed in there, have you installed any xfce apps?

i'm using the gnome desktop & it don't have no libfm anything.

---

### Post by reobedr on 2010-10-13
No xfce apps installed.

also removing the libfm did not solve anything....

Attached a screenshot from the libfm-pref-apps menu...

---

### Post by reobedr on 2010-10-13
Apparently it had nothing to do with the preferred apps, although settings in libfm-pref-apps are still not saved.

After going to the attachments tab in the preferences menu of thunderbird and adding content type: "http" and "https" and pointing those to a browser solved the problem.

I think I'll remove the libfm from the system to avoid having two programs doing the same...

---

