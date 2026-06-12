---
title: "USB drive icon does not appear on desktop"
date: 2011-01-05
forum: General Help
---

### Post by DBQ on 2011-01-05
Hi Everybody. 

I recently started having this annoying problem. 

Previously, whenever I would insert any USB flash drive, an icon for the drive would appear on my desktop. 

Now, the icon does not appear. However, if I go to "Computer", the drive appears there. After clicking on the drive icon in "Computer", the same icon then appears on the desktop. Why is this happening and how do I fix it? Thank you for your help.

P.S. I tried creating a new account to see if the same thing happens, and it does. Is there some way to reset drive mounting settings? Because I also noticed other strange things: i.e. my USB flash drive although inserted, sometimes does not appear in "Computer". When I would insert my SD-card, an icon appears in "Computer" which corresponds to my flash drive, and clicking on it gives the contents of the flash drive (i.e. not SD-card). This is VERY frustrating. Please help me kind people.

---

### Post by Habitual on 2011-01-05
gconf-editor:
/apps/nautilus/desktop/volumes_visible <-- checkmark it.

---

### Post by DBQ on 2011-01-05
Thank you for your help. However, it seems that volumes_visible is already checked. Any other ideas?

---

### Post by DBQ on 2011-01-05
I tried installing updates, but this did not help either.

---

### Post by schwabdale on 2011-01-05
Try installing Ubuntu tweak. There's an option in there to show mounted volumes on the desktop.

---

### Post by DBQ on 2011-01-05
Just tried it. However, the "Show mounted volumes on desktop" is already checked. Thank You.

---

### Post by DBQ on 2011-01-05
I am starting to think that the only way to fix this is to reinstall Ubuntu. Does anybody else have a similar problem?

---

### Post by DBQ on 2011-01-06
I also wonder whether this is simply a gnome issue. However, I just do not know what other settings to try.

---

### Post by DBQ on 2011-01-06
bumpity bump

---

### Post by hardfire_avk on 2011-01-07
/apps/nautilus/desktop/volumes_visible , has always worked for me . maybe its a faulty drive or so, which doesn't get mounted.

---

### Post by DBQ on 2011-01-07
But this happens for all drives -- also the drives appear in "Computer".

---

### Post by DBQ on 2011-01-09
After some intense searching, I discovered that this is a bug in 10.04 (I am running 10.10 so I guess it was not fixed yet).

Some say it is caused by the legacy floppy drive setting in the BIOS (I do not even have a floppy). However, I do not have a floppy drive and do not see such setting in the BIOS (I have ThinkPad T500). I tried doing modprobe -r floppy. This worked for a little then the problem came back.

I tried doing other things such as uninstalling usbmount. This also helped temporarily, but stopped working on reboot. Any ideas?

---

