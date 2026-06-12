---
title: "Window titles enormous"
date: 2012-04-29
forum: General Help
---

### Post by josephellengar on 2012-04-29
Hello, I'm using Gnome 3 Fallback mode and totday I turned on my computer and the titles of all of the windows are enormous. The look like they are size 15-16 font, while before they were 12-14. Where is the setting to change this? I couldn't find it in CCSM or in the system settings dialog. Thanks!

---

### Post by stinkeye on 2012-04-29
Terminal...
```
gconf-editor /apps/metacity/general/titlebar_font
```

or
Install **gnome-tweak-tool**.

---

### Post by josephellengar on 2012-04-29
> **stinkeye said:**
> Terminal...
```
gconf-editor /apps/metacity/general/titlebar_font
```

or
Install **gnome-tweak-tool**.

Thanks! Must have accidentally changed it when I used the tweak tool yesterday. Forgot it was in there.

---

