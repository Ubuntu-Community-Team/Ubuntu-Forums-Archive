---
title: "Take Screenshot disappeared!"
date: 2009-07-04
forum: General Help
---

### Post by XclusiveTurK on 2009-07-04
Hello, I'm new to Linux so excuse me if I'm asking a stupid question.
I've used Take Screenshot only once and it doesn't appear in Applications>Accessories anymore. I think it happened right after I was trying to uninstall Gnome-Do. Any ideas?

---

### Post by Celauran on 2009-07-04
You could try System -> Preferences -> Main Menu and see if it's unchecked. Or you could just use the Print Screen button on your keyboard.

---

### Post by XclusiveTurK on 2009-07-04
Celauran,
Thanks for your suggestion but the thing is I don't really know how to get the screenshot after pressing the PrintScreen button and Take Screenshot was very easy and useful so I will keep searching for the issue...

Thank you very much though.

---

### Post by michy99 on 2009-07-04
Right click on Applications and choose Edit Menus. Click on Accessories and see if Take Screenshot is available but just not checked.

---

### Post by XclusiveTurK on 2009-07-04
Nope, it's not there.

---

### Post by michy99 on 2009-07-04
Well, you can add it as a New Item. The command is:```
gnome-screenshot --interactive
```and the icon is```
/usr/share/icons/gnome/48x48/apps/applets-screenshooter.png
```

---

### Post by XclusiveTurK on 2009-07-04
Michy99,
That definitely resolved the issue thank you very much for your time.

---

