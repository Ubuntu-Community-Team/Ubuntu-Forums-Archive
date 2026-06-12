---
title: "OpenOffice works miserably in Ubuntu 10.04"
date: 2010-05-26
forum: General Help
---

### Post by enverhoxha on 2010-05-26
I have installed Ubuntu 10.04 and many applications have changed, including the OpenOffice suite. Unfortunately, the new OpenOffice Wordprocessor is almost unusable. ODT files open slowly (DOC files are almost better!), and the laptop (T5470 Core2Duo!) seems overwhelmed by this application. I cannot format the text, I cannot zoom, it is real madness. I dont understand why. The previous version was OK. Is there any advice? Could I uninstall this version of OpenOffice (3.2) and return to the older one I used in Ubuntu 8.04?

---

### Post by Mike BFD on 2010-05-26
There was a workaround here in the forums, it helped me to solve this problem so give it a try!

Open any OpenOffice application, go to Tools -> Options, expand the very first menu line (OpenOffice.org).
1. Choose "Memory" and set
- Undo steps: 20
- Use for OpenOffice.org: 128MB
- Memory per object: 20MB
2. Choose "Java" and DISABLE (uncheck) it
Then close all office programs... And open them back to check if this workaround helps.

If using office oftenly, enabling the "quickstarter" is useful, too.

---

### Post by Hagar Delest on 2010-05-26
What you can try:
1. [Reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.
2. Install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

