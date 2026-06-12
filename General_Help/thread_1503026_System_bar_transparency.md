---
title: "System bar transparency"
date: 2010-06-06
forum: General Help
---

### Post by haveacigar on 2010-06-06
In ubuntu I noticed that some apps (vlc, tweetdeck, iplayer) dont allow transparency in the system menu. This isn't a massive issue, although I'd like to know if it is possible to enable transparency, and keep the uniform look.

[IMG]http://imgur.com/HpZ4h.jpg[/IMG]

I've tried changing the icons within the application, however it often refuses to open afterwards...

Cheers in advance for any help.

Ciggy

---

### Post by WorMzy on 2010-06-06
Maybe this link will shed some light on the matter: [http://trac.videolan.org/vlc/ticket/3581]("http://trac.videolan.org/vlc/ticket/3581")


> A transparent icon needs an X11 visual with alpha channel. Unfortunately, VLC needs to disable those otherwise libQt4-gui will use ARGB visuals also for the video widget. This will make VLC essentially unable to play videos.

If you want to hide the notification icon, you can do so by opening VLC, opening Tools -> Preferences, and unchecking Systray icon. Not sure about iPlayer or others though.


EDIT: According to the bottom of that page, they've found a way to allow transparent icons, so it may be in the next version.

---

