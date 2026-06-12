---
title: "Blocked: wine start /unix"
date: 2011-01-07
forum: General Help
---

### Post by Dangerzone812 on 2011-01-07
I got this message when trying to open something with wine:

The file '/home/andrew/Downloads/Setup-Stamp-Editor-v2.5-(R2).exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I know its a clean .exe, is there any way for me to let wine know it's a trusted program?

Thanks in advance, 

Danger

---

### Post by mc4man on 2011-01-07
On a per .exe basis - r. click on the .exe -> properties -> permissions and enable  "Allow exec..."

Or if not wishing to do per .exe
r. click on any .exe -> properties -> open with - other application -> use a custom command.
For command just enter 
wine
In the future use the new option 'wine' instead of 'wine windows program loader'

---

