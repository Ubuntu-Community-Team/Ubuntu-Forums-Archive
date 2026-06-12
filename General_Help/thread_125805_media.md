---
title: "media:/"
date: 2006-02-04
forum: General Help
---

### Post by wilsonisme on 2006-02-04
Before I updated, when I would go here I would see my CD drive, hard drive etc, plus any removable media like iPod, flash stick, whatever. I did a "Full upgrade" in Adept and now it only shows removable media, and my CD drive if there is actually a CD in it.  It doesnt show my hard drive at all.

Is there a way to change it back to how it was before? And is this normal? I liked the old way pre Full upgrade :(

---

### Post by gamma on 2006-02-05
It showed hard drives because someone patched the source code to include that feature. My guess is newer versions don't have that patch. There was a mention of that feature here: [http://www.kdedevelopers.org/node/1789](http://www.kdedevelopers.org/node/1789)

You're going to have to find out what you need to patch, or revert to an older version. Personally I've got nothing showing up in media, unless something is plugged in. No harddrive either..

---

### Post by User_Program on 2006-02-05
This should do the trick.

> sudo adduser hal disk


Now this should show everything in your fstab.  There should be no reason to patch anything or use an older version.  When you update for some reason HAL isn't updated.  I don't know if its a bug or more of just a preference.

---

