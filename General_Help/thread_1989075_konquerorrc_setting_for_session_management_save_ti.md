---
title: "konquerorrc setting for session management save time"
date: 2012-05-28
forum: General Help
---

### Post by sundoulos on 2012-05-28
According to this blog post ([http://edulix.wordpress.com/2008/05/16/konqueror-session-management-crash-handler/]("http://edulix.wordpress.com/2008/05/16/konqueror-session-management-crash-handler/")) there's a setting in konquerorrc to "save session every X seconds". The default is supposed to be 10 seconds.

What's the proper syntax for the setting?

---

### Post by sundoulos on 2012-05-30
Got this over at kubuntuforums if anyone is interested.

[INDENT]Maybe: [https://bugs.kde.org/show_bug.cgi?id=166294](https://bugs.kde.org/show_bug.cgi?id=166294)
...You can change the autosave time editing ~/.kde4/share/config/konquerorrc and adding this:

[SessionManagerSettings]
AutoSaveInterval=2

That would make konqueror autosave every 2 seconds instead of every 10 seconds which is the default value...
With the Kubuntu: ~/.kde/share/config/konquerorrc. Maybe the AutoSaveInterval=0 will disable it ?

A related bug: [https://bugs.kde.org/show_bug.cgi?id=265593](https://bugs.kde.org/show_bug.cgi?id=265593)[/INDENT]

Zero isn't a good value, Konqueror doesn't know what to do with it. But a big number seems to work ok. I used 10000 for starters; doesn't totally disable the feature but sure reduces needless disk activity.

---

