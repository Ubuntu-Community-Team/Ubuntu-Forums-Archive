---
title: "Bootup File System Check seems stuck"
date: 2009-11-29
forum: General Help
---

### Post by held7over on 2009-11-29
This is a Full Install of 9.10.

On Bootup yesterday, my computer wanted to perform a file system check. However, no Percentage Accomplished is shown and the address being scanned does not seem to change either, leaving the routine just blinking the same info on the screen. This morning's bootup is the same. The drive size is 250 gig, so maybe I didn't wait long enough for the check to complete before hitting Esc. Is there a known fix for this?

What is the proper fsck statement I should type into the command line in a terminal to see if this is actually working?

Thanks! :p

---

### Post by held7over on 2009-11-30
This was a false alarm. The information echoed to the screen was ran together giving a % that looked like:

/home (/dev/by-uuid/c3bd5be1-893d-490c-aab7-5e32a2a478621%

It didn't look like anything was changing, but I left it running this morning and came back 30 minutes later and noticed the 21 at the end had changed to a 58 and realized the percentage was just ran together with the rest of the statement. Eventually if finished and booted up.

Sorry about that. I faked myself out.

---

