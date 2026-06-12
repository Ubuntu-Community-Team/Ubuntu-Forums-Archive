---
title: "Ubuntu 9.04 / OpenOffice Spreadsheet Paste issue"
date: 2009-09-03
forum: General Help
---

### Post by Johny79 on 2009-09-03
I've got a very odd problem with OpenOffice Spreadsheets in that I can paste into them using ctrl+v but the options "Paste" and "Paste Special" are greyed out in the main menu and when I right click those options aren't there at all.

A couple of key points..

1) This only happens on existing files, pasting into newly created files works fine until I save, close, and then re-open them.

2) This is happening on three independent Ubuntu 9.04 systems, yet the problem is not present when the files are opened on a Windows based system (tested under XP, Vista & Win7).

I'm hoping someone has an idea of what's going on because quite frankly it's driving me nuts! :confused:

Any help would be much appreciated :)

---

### Post by Johny79 on 2009-09-03
Ok so I've now tried this on another Ubuntu machine running 8.10 and the problem does not occur, also the problem only seems to have been occuring since the kernel updated to 2.6.28-15-geneic recently, I'll try and confirm that shortly.

---

### Post by Hagar Delest on 2009-09-03
Try first to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the official version (from Sun): [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Johny79 on 2009-09-03
How noobish do I feel now :redface:

Deleting the profile has worked on this machine so 99% sure it'll work on the others, and thankfully they weren't massively customised so 10-15 minutes work and all should be well again :)

I seriously cannot thank you enough, hopefully I can return the favour one day!

---

