---
title: "Preventing SD card from opening Nautilus after suspending"
date: 2009-09-04
forum: General Help
---

### Post by tonyr1988 on 2009-09-04
I'm running UNR on a Dell Mini 9 (I think this is applicable to all Ubuntu versions, though). I've got an SD card inserted for extra memory.

I close the lid, go into suspension, and when I open it, nautilus always opens because it re-mounts the SD card. Is there a way to prevent nautilus from opening when mounting external media? I'm sure this is an easy config issue, but I'm having trouble finding it.

---

### Post by Tamlynmac on 2009-09-04
Open Nautilus file browser:

edit/preferences/media

Uncheck box at bottom "Browse media when inserted"

Good Luck & hope this helps.

---

### Post by tonyr1988 on 2009-09-04
> **Tamlynmac said:**
> Open Nautilus file browser:

edit/preferences/media

Uncheck box at bottom "Browse media when inserted"

Good Luck & hope this helps.

That's it. Thanks! I thought there used to be a Gnome menu option for "Removable Drives & Media" so I kept looking for that. I don't know why I didn't think to check in Nautilus.

Thanks again!

---

### Post by Tamlynmac on 2009-09-04
Great, I'm glad it was something simple.

I tend to be real good with simple.... :)


Please show this thread as solved.

---

### Post by tonyr1988 on 2009-09-07
> **Tamlynmac said:**
> Great, I'm glad it was something simple.

I tend to be real good with simple.... :)


Please show this thread as solved.

Actually, it looks like I spoke too soon. I assumed that was correct, since it seemed to be exactly what I wanted. However, I rebooted, verified that my Nautilus setting was still turned off, but it's still doing it. Same behavior as before.

Any other possibilities?

---

### Post by Tamlynmac on 2009-09-07
One last thought you might try is to turn off the auto-mount function in the gnome configuration editor.

system tools/configuration editor/nautilus/preferences/media_automount/uncheck box

Hope this helps...

---

### Post by tonyr1988 on 2009-09-07
> **Tamlynmac said:**
> One last thought you might try is to turn off the auto-mount function in the gnome configuration editor.

system tools/configuration editor/nautilus/preferences/media_automount/uncheck box

Hope this helps...

Same behavior after unchecking the box.

It's not a huge problem -- I can always just close the Nautilus window, but it seems like it's definitely not doing what the preferences say it should be doing. I might file a bug record. It would be for Nautilus, right? Or does some other part of Gnome handle this?

---

### Post by Tamlynmac on 2009-09-08
Yes I believe your correct "Natutilus".

Perhaps, someone else might have an additional idea.

Good Luck.

---

