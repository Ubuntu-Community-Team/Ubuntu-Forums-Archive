---
title: "Thunderbird to open folders, really ? :D"
date: 2012-01-26
forum: General Help
---

### Post by IamInnocent on 2012-01-26
Hello,

for some time now, whenever I chose to open some folder containing a file, in Firefox Download dialog, with a right click on an item in Transmission, etc... Thunderbird pop up a message editor instead. It happens whether I am in a Gnome3 or Xfce session.

Any idea why ?

Thank you. :)

---

### Post by Krytarik on 2012-01-26
Open the file "~/.local/share/applications/mimeapps.list" and simply remove the line for the mime type "inode/directory". That should take care of both Gnome and XFCE, reverting it to the default associations.

Regards.

---

### Post by IamInnocent on 2012-01-27
Thank you Krytarik I did erase the two lines that started by 'inode/directory' and rebooted, but it has no effect.

---

### Post by IamInnocent on 2012-01-27
Me dumb.

It was just a parameter to set up in the prefered applications. 

Ashamed.

---

### Post by Krytarik on 2012-01-27
> **IamInnocent said:**
> It was just a parameter to set up in the prefered applications.
Yeah, I was just about to ask you about that, but the "File Manager" option isn't included there in earlier versions of XFCE, and I've just re-checked that for Oneiric 11.10. If it wouldn't have been there, we would have had to have a closer look at the contents of "~/.local/share/applications/mimeapps.list" and ".../mimeinfo.cache". Nice that it worked out the other way already! :P

---

