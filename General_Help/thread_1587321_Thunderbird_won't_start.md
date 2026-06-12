---
title: "Thunderbird won't start"
date: 2010-10-03
forum: General Help
---

### Post by Ralph L on 2010-10-03
Recently installed Thunderbird 3.1.5. under lucid.  It worked fine.  Tried to install the add-on "Attachment Extractor (AE) (latest version).  When configuring AE to have a default file to extract to, it hung--neither it nor Tbird would respond to anything.  So I used xkill to abort it.  After that TB wouldn't start.  Restarted the computer--TB still wouldn't start.  

If I bring up Terminal and enter "thunderbird -P", it brings up the window to let me choose a profile.  But when I choose my normal profile, it just goes away--no message, no nothing.  I don't know much about logs, but I could find no log with any messages about why TB wouldn't start.

I have a two week old backup of my thunderbird profile, so I created a new profile pointing to the backup thunderbird profile.  This works, but of course, it is two weeks out of date.  I would like to get my current TB profile to work again.

My guess is that, when I xkilled TB, it left some interlock set, that prevents TB from starting.  Does anybody know how to release this interlock, or if it is something else, how to fix it?

Any help appreciated.

Ralph

---

### Post by Ralph L on 2010-10-03
I solved this problem by starting thunderbird under the Terminal using the command "thunderbird -safe-mode".  I had never heard of this option to TB before.  It is not in "man thunderbird".  At any rate this command starts TB with extensions and some other things disabled.  In safe-mode I took out the extensions one by one and found that the offending extension was Lightning 1.0b2.  When I reinstalled Lightning again, it cause TB to be unstartable again.

Ralph

---

