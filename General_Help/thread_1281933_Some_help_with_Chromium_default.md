---
title: "Some help with Chromium: default?"
date: 2009-10-03
forum: General Help
---

### Post by SomeGuyDude on 2009-10-03
Is there a simple way to make Chromium the default browser in Openbox/Compiz? I don't use the various GNOME managers, so I can't set it that way, and it doesn't work via the little menu in its settings.

Secondly, and I think this is the result of it not being the default, it opens everything THROUGH FireFox. I download a torrent, an image, an archive, it opens Firefox before opening the file. Can that be fixed? Thanks.

---

### Post by fragos on 2009-10-04
Changing the Chromium Option to make it the default browser does change that parameter in the Gnome settings for me. If you run by clicking a file icon, say HTML file, then the default opening application is determined by the file Properties. You can change these by right clicking a icon to get a menu of actions for that file type.

---

### Post by eriqjaffe on 2009-10-04
In the terminal...

```
sudo update-alternatives --config x-www-browser
```

It should be pretty obvious from there.

---

