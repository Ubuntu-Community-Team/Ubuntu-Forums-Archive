---
title: "Wine fonts look very ugly"
date: 2012-07-08
forum: General Help
---

### Post by enteon on 2012-07-08
Hello.

I am using Ubuntu 12.04 with KDE4 on two machines and on both I get very ugly fonts in wine right after install. Have a look at the first attachment. The second shows how I expect the fonts to look like and this is about how they look in linux (I like full hinting).

Not all fonts are this ugly though, a few look alright, for example the ones in the config tool. They seem to be a different UI-class of fonts.

Installing fonts and changing aliasing/hinting with winetricks does nothing. Certain amounts of DPI smoothen the fonts out a little, but obviously grow them beyond good taste ^^

Does anyone have any idea what I could do?

Thank you.

---

### Post by chrisauk0 on 2012-07-19
I have noticed the same issue which appeared in wine 1.5.6. Have you tried posting a bug to [http://wiki.winehq.org/Bugs](http://wiki.winehq.org/Bugs)

---

### Post by enteon on 2012-07-19
I think this should not be a bug of wine itself since it shows in really every application and must thus have been spotted by every developer. Therefore I think that this is caused by some software combination specific to ubuntu.

On the other hand: [http://bugs.winehq.org/show_bug.cgi?id=15180  :(]("http://bugs.winehq.org/show_bug.cgi?id=15180")
But on my system both fonts of regedit look ****** :D

I'll have a look into this with the newest dev version when I got more time. And I will test on fedora 17.

Maybe this is just on some systems since close to nobody seems to have stumbled upon this bug in all of the whole wide interwebs :confused:

---

### Post by cottfcfan on 2012-07-27
What version of Wine are you using?
On my system the 1.5x version displays very poor fonts, but this is a development version.
on 1.4x the fonts seem fine.

---

### Post by enteon on 2012-07-27
1.4 is still default on 12.04 and 12.10 thus far.

---

### Post by cottfcfan on 2012-07-27
Fonts are fine here.
Have you got msttcorefonts installed?
When you change the Font are they all the same?

---

### Post by cottfcfan on 2012-07-27
You could also try the font smoothing from here:
[http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)
Although font smoothing should be enabled by default.

---

### Post by enteon on 2012-07-27
msttcorefonts is named corefonts in winetricks, right? I got that. In drive_c/windows/fonts there are lots of TTFs.
Anti-aliasing does nothing.

Ah I can change the fonts. But yes, they all look the same :(

Edit: Ok, some parts of apps do indeed use fonts I can change. But the main parts don't. For example the context menu of miranda's tray icon uses "menu text" but everything in the preferences dialog does not use that nor any other font I can change through winecfg.

PS: "winecfg" show good fonts while "wine uninstaller" shows bad fonts. I think this is a better testcase than some application ^^

---

### Post by cottfcfan on 2012-07-27
Sorry I can't help anymore.
I can't replicate the fonts in your screenshot with any app I use.
Maybe someone else can help.
Have you tried the Wine forum?
[http://forum.winehq.org/](http://forum.winehq.org/)

---

