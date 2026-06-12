---
title: "Netscape Plugin doesn't load (Ubuntu 64bit)"
date: 2011-06-14
forum: General Help
---

### Post by o.martin on 2011-06-14
Hello,

i have the following problem: i found out (or i make a mistake) that our netscape plugin doesn't load in firefox 4.0.1 from the directory (/usr/lib/mozilla/plugins, /usr/lib64/mozilla plugins). But if i copy the netscape plugin to /usr/lib/firefox-4.0.1/plugins it works fine.

My Target Platform was Ubuntu 11.0.4 x64.
On my Ubuntu 11.0.4 x86 all works fine from /usr/lib/mozilla/plugins

Does i do anything wrong, or is there a path missing from the preinstalled firefox script

best regards,
martin

---

### Post by pqwoerituytrueiwoq on 2011-06-14
you would need to use a plugin wrapper like we did with flash before we got a 64bit version
64bit browser can't use a 32bit plugin natively

---

### Post by o.martin on 2011-06-14
thx for the fast answer:

it is a 64 bit netscape plugin. Chrome could load it without problems from /usr/lib64/mozilla/plugins but firefox only load the plugin from /usr/lib64/firefox-4.0.1/plugins. 

we have for a 32 bit environment seperate plugins, cause the wrapper has some problems sometimes with our plugin.

---

