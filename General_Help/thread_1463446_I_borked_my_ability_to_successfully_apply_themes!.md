---
title: "I borked my ability to successfully apply themes!"
date: 2010-04-27
forum: General Help
---

### Post by mjpatey on 2010-04-27
Long story short:  I wanted to change the theme of elevated-privilege windows to something nicer than the GNOME default.  I received two suggestions from the forums... first attempt was to install and run "gtk-chtheme" using gksudo.  This did change things, but used an odd UI that didn't seem to change everything.  Second attempt was to run "gksudo gnome-appearance-properties", which worked perfectly.

Well, now I can't properly change the theme of my normal user.  Some themes change some elements, and other themes change other elements... sometimes when flipping through themes to preview them, an element from one theme gets inherited by the next theme I preview (e.g. the background color behind the "controls")... and I end up with an odd hybrid of 2 themes.

Can I somehow wipe the whole thing and start fresh?  I have no idea what I might have done!  Thanks in advance for any light you can shed.

-Mark

---

### Post by elliotn on 2010-04-27
try deleting the .theme folder in your home folder uhmmm not sure it would work but worth a try btw it will erase all ur themes

---

### Post by towheedm on 2010-04-28
> **mjpatey said:**
> Long story short:  I wanted to change the theme of elevated-privilege windows to something nicer than the GNOME default.  I received two suggestions from the forums... first attempt was to install and run "gtk-chtheme" using gksudo.  This did change things, but used an odd UI that didn't seem to change everything.  Second attempt was to run "gksudo gnome-appearance-properties", which worked perfectly.

Well, now I can't properly change the theme of my normal user.  Some themes change some elements, and other themes change other elements... sometimes when flipping through themes to preview them, an element from one theme gets inherited by the next theme I preview (e.g. the background color behind the "controls")... and I end up with an odd hybrid of 2 themes.

Can I somehow wipe the whole thing and start fresh?  I have no idea what I might have done!  Thanks in advance for any light you can shed.

-Mark

If you can make a short story a bit longer, it might help others to help you.  The command
```
gksudo gnome-appearance-properties
```

should not affect other user or screw with your themes.  It could have have been something to did previously with gtk-chtheme.  Could you explain a bit further exactly what was done starting from the beginning ie installing gtk-chtheme.

---

