---
title: "how does one know what flash version one has?"
date: 2010-10-13
forum: General Help
---

### Post by princeofnam on 2010-10-13
i want to see if i have 32 or 64 bit flash installed on my computer, but i'm not exactly sure how

---

### Post by efflandt on 2010-10-13
Even if you have a 64 bit system, if you installed flashplugin-installer, or if that was installed as part of ubuntu-retricted-extras or similar, you end up with 32-bit flash (with nswrapper in a 64-bit system).

For real 64-bit flash you would need to uninstall flashplugin-installer, get 64-bit flash from [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/) then extract that, and use **sudo** to **cp** or **mv** the extracted **flashplayer.so** to something like** /usr/lib/mozilla/plugins**.

Another clue, if Firefox Tools > Add-ons > Shockwave Flash shows a version 10.1 r85 or lower, you likely have 32-bit flash.  Current 64-bit flash I thought was 10.2 r161 (in Lucid), although, for some reason Maverick now displays it as 10.2 d161.  That has worked fine for me in Firefox, but for 64-bit Hulu Desktop, I had to tell ~/.huludesktop where to find flash at /usr/lib/mozilla/pluging/flashplayer.so.

---

