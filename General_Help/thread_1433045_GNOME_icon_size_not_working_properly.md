---
title: "GNOME icon size not working properly"
date: 2010-03-18
forum: General Help
---

### Post by mikesir87 on 2010-03-18
One day, I was altering the size of the icons to make them smaller.  I first made them larger (to 150%), and then shrunk them down to 66%.  I did this through Nautilus while being in the /var/www folder.  The Desktop icons resized down to the 66%, as well as all other icons.  However, the icons in the /var/www folder remained large (at the 150%).  I've tried changing it, and no change occurs in the particular folder.  Are there any ideas on what I can do, and how to fix it?

Thanks!

---

### Post by mastermindg on 2010-03-18
Have you tried gconf-editor?

Under /apps/nautilus/icon_view.

---

### Post by mikesir87 on 2010-03-18
I hadn't tried it, but just did.  I tried to change the 'thumbnail_size', and all other icons changed.  But, not the ones in this particular folder.  Is there any way to set settings for a single folder?

---

