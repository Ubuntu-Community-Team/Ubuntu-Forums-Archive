---
title: "Chromium gestures not working (Ubuntu 11.04/Xubuntu 11.10)"
date: 2012-04-23
forum: General Help
---

### Post by zhvihti on 2012-04-23
I used Smooth Gestures without an issue. Installed yesterday Xubuntu 11.10, installed latest Chromium (18.0.1025.151, Developer Build 130497), Smooth Gestures was gone and nowhere to be found on the Chrome Market. Every other gesture plug-in I tried doesn't work and the issue seems to be the context menu - it comes up immediately upon clicking the right mouse button (on mousedown, rather than mouseup). I can see the mouse trails underneath but nothing happens.

Removed Chromium, got the stable Google Chrome from the website (again version 18 ) - same issue. Loaded up Ubuntu 11.04 with the same Chromium version (I think it had an update yesterday) - and the same thing - Smooth Gestures is gone, and I cannot find it anywhere. All other plugins do not work, and again due to the context menu.

There seems to be no option neither in Chrome nor in Gnome to somehow make the context menu pop-up on mouseup. The "Suppress context menu, when gesture failed" in "Gestures for Chrome" seems to do nothing.

Tried also deleting the user and starting with a clean profile - same thing.

---

### Post by LewisTM on 2012-04-23
Google has caught [malware]("http://codeonfire.cthru.biz/?p=96") code in the extension and so has deleted it from its Web Store. The malware would report user web tracking to a website. The site has gone down so no worries.

I found a hacked version [here]("http://nisza.org/chromium/smooth-gestures-0.15.4.crx") that would supposedly not contain the malware. You also need this [plugin]("http://nisza.org/chromium/smooth-gestures-plugin-0.8.crx") to make the right click menu work. Use at your own risk.

---

### Post by zhvihti on 2012-04-24
Thanks a lot! That worked marvelous.

Even though I searched, I couldn't find this hacked version.

---

### Post by strungoutfan78 on 2012-08-26
> **LewisTM said:**
> Google has caught [malware]("http://codeonfire.cthru.biz/?p=96") code in the extension and so has deleted it from its Web Store. The malware would report user web tracking to a website. The site has gone down so no worries.

I found a hacked version [here]("http://nisza.org/chromium/smooth-gestures-0.15.4.crx") that would supposedly not contain the malware. You also need this [plugin]("http://nisza.org/chromium/smooth-gestures-plugin-0.8.crx") to make the right click menu work. Use at your own risk.

Seriously, thank you for this.  I just spent the vast majority of my day test driving other browsers because:
[LIST=1]
[*]**Chromium** - on Debian (I don't actually use Ubuntu, just here for the huge knowledge base) is so far behind as far as the version.  And it constantly crashes.  Facebook doesn't work.
[*]**Iceweasel** - Constantly crashes.  Facebook doesn't work.
[*]**Galeon** - Constantly crashes and has no plugins.  Facebook doesn't work.
[*]**Firefox 14** - Facebook actually works great but it has been severely altered (coming from Iceweasel) to the point that I have not the slightest clue how to get ANY plugins working (although youtube videos play fine :confused:)
[*]**Chrome** - Facebook works, but I couldn't use my Smooth Gestures that I've used for so long with Chromium.  No gestures = miserable browsing experience for me.
[/LIST]

Thank you, thank you, thank you.:guitar:

---

### Post by thewump on 2012-11-06
Oh man.. thank you so much!

K

---

