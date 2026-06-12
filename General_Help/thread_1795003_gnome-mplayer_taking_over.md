---
title: "gnome-mplayer taking over?"
date: 2011-07-01
forum: General Help
---

### Post by Iancsb on 2011-07-01
I don't know how it started but now whenever I try to open my documents, pictures, music and so on it always opens it with gnome-mplayer. I don't have any idea about what to do to fix this, any help would be appreciated.[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by mc4man on 2011-07-01
Post the contents of this file and please mention what release of ubuntu you're using. (there is a small diff between 10.04 (lucid) and 10.10,11.04 in this regard

```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by nrundy on 2011-07-02
> **Iancsb said:**
> I don't know how it started but now whenever I try to open my documents, pictures, music and so on it always opens it with gnome-mplayer. I don't have any idea about what to do to fix this, any help would be appreciated.[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

Couple things you can try:
1. System - Preferences - Preferred Applications

2. right-click a file type (eg. mp3 file) and then click the tab OPEN WITH and select what program you want that file type to always open with.

---

