---
title: "unison sync between ubuntu and windows"
date: 2010-02-19
forum: General Help
---

### Post by sam.666 on 2010-02-19
hi.  i set up ssh and unison on my windows machine and i am trying to do a sync on my ubuntu machine to windows.

i am running into some issues.

certain paths give me the following error:

Error: The path Music/Xxxx is ambiguous (i.e., the name of this path or one of its ancestors is the same, modulo capitalization, as another path in a case-sensitive filesystem, and you are synchronizing this filesystem with a case-insensitive filesystem. 

When i search for Xxxx on my ubuntu system i only see it in that one Music/Xxxx location.

after giving this error, unison aborts.

suggestions?

---

### Post by dcstar on 2010-02-19
> **sam.666 said:**
> hi.  i set up ssh and unison on my windows machine and i am trying to do a sync on my ubuntu machine to windows.

i am running into some issues.

certain paths give me the following error:

Error: The path Music/Xxxx is ambiguous (i.e., the name of this path or one of its ancestors is the same, modulo capitalization, as another path in a case-sensitive filesystem, and you are synchronizing this filesystem with a case-insensitive filesystem. 

When i search for Xxxx on my ubuntu system i only see it in that one Music/Xxxx location.

after giving this error, unison aborts.

suggestions?

Linux uses case-sensitive filesystems, Windows may not.

---

