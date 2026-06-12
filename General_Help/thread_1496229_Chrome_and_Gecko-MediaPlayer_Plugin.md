---
title: "Chrome and Gecko-MediaPlayer Plugin"
date: 2010-05-29
forum: General Help
---

### Post by gerowen on 2010-05-29
The speed difference between Firefox and Google Chrome is just unreal, however I have one main problem.  Google Chrome refuses to detect my gecko-mediaplayer plugin for MPlayer, and the totem embedded player won't play some videos, i.e. the streaming video of the oil spill on BP's website.  Help please.

---

### Post by gerowen on 2010-05-29
"Chromium" does work with it however, so I guess I'll be using Chromium for now.

---

### Post by lovinglinux on 2010-05-29
> **marcusdean.adams said:**
> The speed difference between Firefox and Google Chrome is just unreal

[See this](http://lovinglinuxblog.blogspot.com/2010/05/browser-speed-test.html).

---

### Post by daniele80 on 2010-06-21
I have the same problem.
Chromium doesn't detect gecko-mediaplayer on Ubuntu 10.04

---

### Post by eklapothik on 2010-09-15
+1 on that.

Using Chromium 6.0.472.53 on Ubuntu 10.04 (lucid)

If I try to browse any site that has media player it just shows missing plugin. I tried copying the plugin directory contents of mozilla to chromium directory. It did not work.

---

### Post by aim on 2010-10-01
Maverick - +1 for non-working list

---

### Post by voutasaurus on 2010-10-20
+1 for Chrome (stable) on Ubuntu 10.04

---

### Post by gmutlu on 2010-11-21
I found out that it was blacklisted:
[http://code.google.com/p/chromium/issues/detail?id=24507](http://code.google.com/p/chromium/issues/detail?id=24507)

So, if you want to give a try just rename the gecko* files to anything in /usr/lib/mozilla/plugins/

---

### Post by davirrirri on 2011-01-16
> **gmutlu said:**
> I found out that it was blacklisted:
[http://code.google.com/p/chromium/issues/detail?id=24507](http://code.google.com/p/chromium/issues/detail?id=24507)

So, if you want to give a try just rename the gecko* files to anything in /usr/lib/mozilla/plugins/

Thank you very much! I didn't knew how fix this. Rename the gecko* files works, but should be: Gecko*, with "G" majuscule to work well.
However, the gecko-mediaplayer grafically doesn't look good in KDE, but works :)

Edit: With "G" or other rename file equally the plugin fails, in my case (I use KDE). I can listen the stream audio but the control plugins I can't see :(

---

