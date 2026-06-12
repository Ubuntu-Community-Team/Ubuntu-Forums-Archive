---
title: "Unusual timestamp issue when moving files"
date: 2010-03-10
forum: General Help
---

### Post by KingAlanI on 2010-03-10
Files created or edited on my Ubuntu machine that are copied to a flash drive and then onto a Windows machine end up displaying an unusual timestamp.
This is a few hours ahead of when the file was actually last modified; I haven't noticed any specific gap

Timestamps look fine when I create/edit the files.
Files themselves are OK.
System clock appears to be set correctly.

Not a problem when moving stuff in the Windows-->Windows or Windows-->Linux directions

9.04 and XP

---

### Post by dcstar on 2010-03-10
> **KingAlanI said:**
> Files created or edited on my Ubuntu machine that are copied to a flash drive and then onto a Windows machine end up displaying an unusual timestamp.
This is a few hours ahead of when the file was actually last modified; I haven't noticed any specific gap

Timestamps look fine when I create/edit the files.
Files themselves are OK.
System clock appears to be set correctly.

Not a problem when moving stuff in the Windows-->Windows or Windows-->Linux directions

9.04 and XP

File timestamps are all in UTC, if they display differently on other systems then the Time Zone offsets that those system run are incorrect.

---

### Post by KingAlanI on 2010-03-22
Does the time zone offset relate to what the system clock displays, or do I have to look it up on each system some other way?

---

