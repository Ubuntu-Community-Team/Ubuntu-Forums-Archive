---
title: "OpenOffice crash when trying to open a word file"
date: 2010-02-25
forum: General Help
---

### Post by mrpenguin on 2010-02-25
I have a word file that i transfered to my ubuntu laptop, when i copied it here it was changed to a rtf file
When i try to open this file Openoffice opens up but then immediately freezes and when I click on quit it tells me openOffice is not responding.
I just did an update and its still doing the same .. any idea ??

---

### Post by CharlesJWelsh on 2010-02-25
I would mark for complete removal and reinstall it. Try that.

---

### Post by Hagar Delest on 2010-02-26
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

But if Ubuntu has changed the file to .rtf, then it means that it was not a true .doc file. Windows clumsily relies on the extension whereas GNU/Linux looks at the file header. Remove the extension to see what is the true format.

NB: RTF support is rather flaky in OOo.

---

### Post by BZF on 2010-02-26
[COLOR="Blue"]Do remove and reinstall. If that doesn't work, just remove it and try a different version[/COLOR]

---

