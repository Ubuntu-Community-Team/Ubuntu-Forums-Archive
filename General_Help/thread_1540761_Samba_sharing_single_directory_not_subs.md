---
title: "Samba sharing single directory not subs"
date: 2010-07-28
forum: General Help
---

### Post by SagnaB on 2010-07-28
[SIZE=2]I have samba set up and working quite well, but I have several shared  directories containing multiple directory trees, and for some reason the  sub-directories of the shared one are not shared.
Is there a way do set them to shared automatically rather than having to  go through and set share for each and every one?[/SIZE]

---

### Post by prodigy_ on 2010-07-28
What do you mean by "not shared". Are they invisible to remote users or just not accessible?

---

### Post by SagnaB on 2010-07-29
Not accessible. (Permission errors) The share settings seem to only apply to the shared directory and the FILES within but not the sub's.

---

### Post by pricetech on 2010-07-29
Check local permissions to make sure they're not restricted that way.

What permissions do you have on the root share ??

---

### Post by SagnaB on 2010-07-29
SOLVED

When I right-clicked>Properties>Permissions I noticed I button at the bottom labelled "Apply permissions to enclosed files". Clicking that Solved it!

Thanks!

---

