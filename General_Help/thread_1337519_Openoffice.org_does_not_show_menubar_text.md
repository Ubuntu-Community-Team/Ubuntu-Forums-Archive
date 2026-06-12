---
title: "Openoffice.org does not show menubar text"
date: 2009-11-25
forum: General Help
---

### Post by evilgeniuself on 2009-11-25
For some reason, after I switched to Ubuntu 9.10, openoffice started to have problems. Basically, all text that was not part of the document had turned into striped bars and such! I have pictures below, and could really use some help solving this problem...

[[IMG]http://img340.imageshack.us/img340/7488/screenshotdq.th.png[/IMG]](http://img340.imageshack.us/i/screenshotdq.png/)[[IMG]http://img204.imageshack.us/img204/1560/screenshot1dm.th.png[/IMG]](http://img204.imageshack.us/i/screenshot1dm.png/)[[IMG]http://img204.imageshack.us/img204/8700/screenshot2q.th.png[/IMG]](http://img204.imageshack.us/i/screenshot2q.png/)[[IMG]http://img340.imageshack.us/img340/4439/screenshot4jq.th.png[/IMG]](http://img340.imageshack.us/i/screenshot4jq.png/)

---

### Post by Hagar Delest on 2009-11-27
See that one, several fixes (read until the end): [[Solved] No text in OpenOffice menus](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183).

---

### Post by evilgeniuself on 2009-11-28
I tried anti-aliasing, through the toolbar method, and it still didn't work. I would like to upgrade my computer when the next distro comes out, so uninstalling all the OpenOffice packages is not a good idea. I don't think I have an NVidia driver, although I'm not 100% certain, so the driver option wouldn't work. Lawfer's suggestion by "TexasRanger" also did nothing except make the titlebar bolded... Is there another approach I could try?

---

### Post by Hagar Delest on 2009-11-28
Basically, upgrading the distro with the mere upgrade feature is not that good. Former files usually remain and can cause problems afterward. I've already tried that and it has been reported several times in forums. Better reinstall from scratch (but it means that the partitioning system was good to avoid data loss).

And even if you remove the OOo packages, you can reinstall them before upgrading the distro (you'll need to remove the Sun version before of course).

---

### Post by evilgeniuself on 2009-11-30
Ok, so I tried installing the sun version, and apparently it worked. The problem is that I cannot find the application.....

---

### Post by Hagar Delest on 2009-11-30
Have you tried soffice in a terminal? Have you installed the package in the desktop-integration sub-folder of the DEBS folder?

---

