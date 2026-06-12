---
title: "Why is my gnome composting/Cairo Dock not working properly?"
date: 2011-01-01
forum: General Help
---

### Post by miserablecreat on 2011-01-01
Hello.  Im running Linux Mint Debian Edition.  I have also installed Cairo Dock.

At first there was a black box for a background, but when I turned on the gnome composting, I got the transparent background that I wanted.  I turned on the gnome composting by going to control center/desktop settings/Windows/Use Gnome Composting.

It was fine for about a day.

Then all of a sudden I am back to the black box.  I checked the gnome composting check-box and it is still checked.  I don't know what else to try.

Perhaps I need to install my graphics driver for my graphics card and use Compiz.  I would rather not bother jumping through those hoops if I can help it.  Bottom Line -- Gnome Composting is Broken!

Any help  would be greatly appreciated!

---

### Post by stinkeye on 2011-01-01
alt+F2 and enter
```
gconf-editor
```
Hit run.

check the key
```
/apps/metacity/general/compositing_manager
```

---

