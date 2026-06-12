---
title: "Problem with GNOME Desktop"
date: 2010-05-03
forum: General Help
---

### Post by hyeeeeeeeeelp on 2010-05-03
When i logged into a gnome desktop i got this message:
"The GNOME session manager was unable to read file:'/home/(desktop name)/ICEauthority'. If this file exists it must be readable by you for GNOME to work properly.  try logging in with failsafe session and removing the file." What commands do i use for that? or do i need to do something else?

---

### Post by steveneddy on 2010-05-03
from a google search:

[http://ubuntuforums.org/archive/index.php/t-1583.html](http://ubuntuforums.org/archive/index.php/t-1583.html)

---

### Post by WorMzy on 2010-05-03
Does the output end there, or do you get a login prompt?

If no prompt:

Restart, and choose to boot in recovery mode from the grub menu. Wait for it to ask you what to do, then choose "drop to root shell" (or words to that effect). Next enter:
```
mv /home/(desktop name)/ICEauthority /home/(desktop name)/ICEauthority.bak
``` then restart.

ELSE

If you get a login prompt, log in, then do the above command.

---

