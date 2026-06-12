---
title: "Can't use Java in Midori Web Browser?"
date: 2010-02-13
forum: General Help
---

### Post by PsychoDevon on 2010-02-13
I have switched from Firefox to Midori, but the default Java plugin in the Software Center will not work in Midori. I'm using Ubuntu 9.10 64-bit.

---

### Post by lykeion on 2010-02-17
I bump this..

Been doing some research but it seems that midori and webkit browsers in general have problems to load the java plugin.
Midori uses netscape plugins in the folder /usr/lib/mozilla/plugins and even though there is a shortcut to libjavaplugin.so / libjavaplugin_oji.so in that folder the plugin does not load in midori. Flash plugin works ok though.

Is there a solution to this or is it because midori/webkit is still under development?

---

### Post by GhostLyrics on 2010-02-21
Java support for Midori is not yet available. In other terms: you can't use it even if the plugin is there.

---

