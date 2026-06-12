---
title: "Share Sunbird and Lightning local calandars."
date: 2009-08-21
forum: General Help
---

### Post by ajgreeny on 2009-08-21
I run Thunderbird with the lightning calendar add-on, and wanted to also have Sunbird on the same machine and sharing the same calendar information, but I couldn't see any way from the preferences to do this in either application.

A quick search of the mozilla website showed me that the calendar data is stored in a file called storage.sdb, an sqlite 3 database in the user profile of each application.  I therefore made a link from the ~/,mozilla/sunbird/XXXXXX.default/storage.sdb to the same named file in the ~/.mozilla-thunderbird/XXXXXX.default folder, which is already full with lots of lightning calendar data.

Bingo, I now have the same data appearing in both the thunderbird lightning add-on and the sunbird stand-alone version.  I just thought it worth sharing this information as others may want the same, but not have found how to do it.

---

### Post by powerfade1 on 2009-08-25
Thanks for the info, but how do you make a "link?"  Thanks!

---

### Post by j.bell730 on 2009-08-25
Type this in terminal and read up :).
```
man ln
```

---

### Post by powerfade1 on 2009-08-25
Thanks!

---

