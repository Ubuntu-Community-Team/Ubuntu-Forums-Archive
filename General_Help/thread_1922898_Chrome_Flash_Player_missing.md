---
title: "Chrome Flash Player missing"
date: 2012-02-09
forum: General Help
---

### Post by whalogreg on 2012-02-09
I just installed the chrome deb from google's website on a fresh install of 11.10. For some reason flash is missing. I looked in chrome://plugins and no flash player there... Am I missing something? Shouldn't chrome come with flash built-in?

---

### Post by gandaran on 2012-02-09
> **whalogreg said:**
> I just installed the chrome deb from google's website on a fresh install of 11.10. For some reason flash is missing. I looked in chrome://plugins and no flash player there... Am I missing something? Shouldn't chrome come with flash built-in?
if chrome is 64-bits version you have to install flash preferably 64-bits flash as only the 32-bits chrome does have it built-in.

---

### Post by Pilot6 on 2012-02-09
> **gandaran said:**
> if chrome is 64-bits version you have to install flash preferably 64-bits flash as only the 32-bits chrome does have it built-in.

This is not true. Flash is built in all versions of Chrome. 32 or 64 bit. Yoy can check it here.
[http://kb2.adobe.com/cps/155/tn_15507.html](http://kb2.adobe.com/cps/155/tn_15507.html)

---

### Post by gandaran on 2012-02-09
> **Pilot6 said:**
> This is not true. Flash is built in all versions of Chrome. 32 or 64 bit. Yoy can check it here.
[http://kb2.adobe.com/cps/155/tn_15507.html](http://kb2.adobe.com/cps/155/tn_15507.html)
since when?
google it, only linux chrome 32-bits has it built-in unless there's a recent version that I do not know of.

---

### Post by efflandt on 2012-02-09
If you have a version of Chrome without the flash plugin, it should automatically use the flash plugin for firefox or mozilla, if you installed that.  Did you install **ubuntu-restricted-extras** (which includes flash), OR **flashplugin-installer**, OR put the 64-bit libflashplayer.so in a /usr/lib/firefox, firefox-addons or mozilla **plugin** directory?

---

