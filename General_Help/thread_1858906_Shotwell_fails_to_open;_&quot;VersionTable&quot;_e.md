---
title: "Shotwell fails to open; &quot;VersionTable&quot; error?"
date: 2011-10-13
forum: General Help
---

### Post by zipmon on 2011-10-13
Hi! Hoping someone can help me out here, I'm running up-to-date 11.04 and as of this morning, clicking on Shotwell in the launcher just makes the icon glow for a few seconds, but won't actually start the application. I tried starting it in the terminal and I got this:


> morgan@morgan-starling:~$ shotwell
**
ERROR:i686-linux-gnu/db/VersionTable.c:104:version_table_construct: assertion failed: (res == SQLITE_OK)
Annullato


If anyone knows how to sort this out, it'd be much appreciated!

Thanks! :)
-Morgan

---

### Post by zipmon on 2011-10-13
If this ever affects anyone else, I found the culprit & it's not a happy ending.

As per [this bug report]("http://redmine.yorba.org/issues/3458") on the developer's page, looks like the database got corrupted in a crash, and there's nothing to be done about it - 6 months of tagging 10,000+ photos, down the proverbial drain! This issue was apparently fixed in version 0.10.0, by backing up the database everytime you close the program, but since the Natty repository's still on 0.9.3, that patch never made its way down to my poor computer.

Lame! :(

---

