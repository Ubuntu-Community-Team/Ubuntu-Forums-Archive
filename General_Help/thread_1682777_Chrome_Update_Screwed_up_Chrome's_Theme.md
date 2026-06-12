---
title: "Chrome Update Screwed up Chrome's Theme"
date: 2011-02-06
forum: General Help
---

### Post by Joseph Schwenker on 2011-02-06
Yesterday, I installed an update to Chrome, only to find that my once perfect Chrome theme had been screwed up. Originally, Chrome's tab bar had matched my title bar, and everything looked fine, as I use Elementary. Now, the tab bar has turned blue, highly contrasting my gray titlebar. I'm using Chrome's GTK theme with native borders. I could use the Elementary chrome theme, but that doesn't use the GTK icons, which I love. This is a minor issue, but it's annoying, as Chrome looked fine until yesterday.

---

### Post by Brandon Williams on 2011-02-07
I installed gtk-chtheme and used it to select the gtk theme that was already selected in my window manager. Then I added the following ~/.gtkrc.mine file:```
style "chrome-gtk-frame"
{
    ChromeGtkFrame::frame-color = "#3C3C3C"
    ChromeGtkFrame::inactive-frame-color = lighter("#3C3C3C")
}
class "ChromeGtkFrame" style "chrome-gtk-frame"
``` Where "#3C3C3C" is the expected color for the tab bar when the window is in focus. The out-of-focus window's tab bar isn't quite right yet, but, this gives me the ability to make changes anyway.

---

### Post by Joseph Schwenker on 2011-02-07
I added that file, but I am not seeing a change. I specified "#D9D9D9" for the color.

---

### Post by Brandon Williams on 2011-02-08
Do you also have a .gtkrc-2.0 file? This would be created by gtk-chtheme and will pull in .gtkrc.mine. I use gtk-chtheme because opening it and clicking apply will cause any changes that I make to .gtkrc.mine to be applied immediately, even if I don't actually change the main theme.

---

