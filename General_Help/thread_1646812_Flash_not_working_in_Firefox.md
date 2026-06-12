---
title: "Flash not working in Firefox"
date: 2010-12-16
forum: General Help
---

### Post by beastrace91 on 2010-12-16
So I've installed the **flashplugin-nonfree** package but for some reason flash refuses to work under Firefox. The libflashplayer.so is in the right folder and flash actually works under Chromium browser - just not Firefox.

I setup the system from a 10.04 32bit minimal CD could it just be a pakage I am missing that is causing flash not to work under Firefox? I've tried Firefox 3.6.x and 4.0 beta and flash fails in both.

Ideas?
~Jeff

---

### Post by sikander3786 on 2010-12-16
First of all, I would suggest to use the flash-aid FF plugin as it would remove any conflicting plug-ins and install the appropriate one's.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
courtesy of forum member *lovinglinux*

---

### Post by efflandt on 2010-12-16
What does Firefox show for "Shockwave Flash" under Tools > Add-ons > Plugins?  There should only be one version.

Not exactly sure what **flashplugin-nonfree** does, because it used to sometimes install an older transitional flash version, although, it may just install **flashplugin-installer,** which is what you would normally install directly for 32-bit flash.  Or **ubuntu-restricted-extras** includes flashplugin-installer, codecs, and things related to audio/visual and browsing.

Make sure that you have NOT also installed gnash or something else that may conflict with adobe flash.

---

### Post by beastrace91 on 2010-12-16
That firefox addon did NOT do the trick. Gnash/anything else of that nature is not installed on the system currently. There are no plugins listed under Firefox as installed -

[IMG]http://i.imgur.com/Ce0JL.png[/IMG]

Any ideas? As I said - the .so file is on the system and works under Chromium - I just much prefer firefox :(

~Jeff Hoogland

---

### Post by beastrace91 on 2010-12-16
LOL. Issue resolved (mostly) my local folder in **~/.mozilla** was called **plugin** instead of **plugins**. Renaming it solved the issue. Odd that Firefox cannot find the system shared folder for flash like Chromium though.

~Jeff

---

