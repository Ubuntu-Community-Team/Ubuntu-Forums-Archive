---
title: "I can't change fonts in system settings"
date: 2011-09-27
forum: General Help
---

### Post by TubbyT on 2011-09-27
I was changing fonts in my system settings under Appearance. Done it several times with no problems. Switched to one font, didn't like it, went to change it and when I go to System Settings > Appearance, it won't let me click the font tab. I've tried rebooting several times with no change. I can't click the background or fonts tab under appearances. Not only that, it won't let me close the window either.

HELP!

---

### Post by Krytarik on 2011-09-27
Let's see if this is confined to the font settings. Try resetting them all to the defaults:
```
gconftool-2 --unset /desktop/gnome/interface/font_name
gconftool-2 --unset /desktop/gnome/interface/document_font_name
gconftool-2 --unset /desktop/gnome/interface/monospace_font_name
gconftool-2 --unset /apps/nautilus/preferences/desktop_font
gconftool-2 --unset /apps/metacity/general/titlebar_font
```Hope it works!

---

