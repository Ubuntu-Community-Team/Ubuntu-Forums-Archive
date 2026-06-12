---
title: "Mlti Screen Focu stealing"
date: 2009-10-26
forum: General Help
---

### Post by .Sook on 2009-10-26
Ok here's the issue.. starting to really annoy me and frankly the fact there's no option to disable this is disturbing...

Have dual-screens, each running seperate xsession...

Screen 0 - runs compiz - does browsing and everything else

Screen 1 - doesnt run compiz - jus runs vlc player

I have VLC on screen 1 - playing a playlist...  the problem is that every time it plays a new file, the keyboard focus and mouse focus are stolen to that screen, which is 100% annoying....

The only way to get keyboard focus back to screen 0 is by double-clicking on a pidgin contact...

Someones surely got a solution to this ?

---

### Post by .Sook on 2009-10-27
bump

---

### Post by Giblet5 on 2009-10-27
You can't run compiz in only one logical screen (eg, DISPLAY=:0.0 or DISPLAY=:0.1).

Compiz runs on a display and all of that display's screens run compiz or none of them do.

You'll probably have to disable compiz.

---

### Post by .Sook on 2009-10-27
well it worked fine in 8.10 - so i diagree...

---

