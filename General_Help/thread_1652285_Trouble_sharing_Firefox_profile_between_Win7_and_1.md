---
title: "Trouble sharing Firefox profile between Win7 and 10.10"
date: 2010-12-24
forum: General Help
---

### Post by BKbroila on 2010-12-24
I recently got Ubuntu 10.10 working, and tried sharing my FF profile between Win7 and 10.10, which I am dual-booting. The profile folder is on my Windows partition, and I've set my Firefox in Ubuntu to lookup that exact folder directory in the Windows Partition. However, it never works. If I try opening up FF in 10.10, I get a prompt that FF is already open and that I should close all windows, even though I just cold-booted.
Any help?
Should I put my FF profile on a different partition (i have a storage partition where I put all my documents and media)?

---

### Post by noah++ on 2010-12-24
The error could be a red herring, given [this unresolved six-year old bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=278860"). In any case, can you go through [this checklist]("http://kb.mozillazine.org/Profile_in_use") and see if any of it helps?

---

### Post by BKbroila on 2010-12-31
Oh I think I now why this is happening.
It's since the profile is located on another partition, it can't find it, so it automatically says it's locked.
I have this problem with a shortcut I have on my desktop on Ubuntu. It points to a folder on another partition labeled Storage and whenever I dbl click it, it says the location is invalid

So anybody know how to have Ubuntu look-up or recognize all of my partitions when I boot up?
I think if I get Ubuntu to recognize all the partitions at boot-up, I won't have any of those problems

---

### Post by mike555 on 2010-12-31
You might just be better off using "Firefox Sync" addon.

---

### Post by BKbroila on 2010-12-31
Eh. I'd rather not use Sync, as it seems like an inconsistent option.

---

