---
title: "HELP unable to mount filesystem"
date: 2010-06-24
forum: General Help
---

### Post by Hawk666 on 2010-06-24
sooo i seem to have run into a big problem, luckily i'm dual booted with windows and am able to seek help. Anyways when I try to boot into Ubuntu 9.10 the first thing that happens is this:

Filesystem checks are in progress

I have seen this on a few occasions and thought nothing of it, I have let them complete in the past and was able to boot no problem, but recently that has changed, whether or not I let the checks complete I get the following error:

Mount of filesystem failed.43708f-0498-4699-9fd5-1f52df0bc181
A maintenance shell will now be started.

Any thoughts on recovering this partition or at least gaining enough access to it to backup some data?

---

### Post by rudy.b on 2010-06-24
Hi,

When the maintenance shell starts, you should see a message to the effect of, "Press CTRL-D to retry" and a root prompt below it.  You might try running "fsck" manually at the maintenance shell, follow the prompts, and press CTRL-D when it completes.

---

### Post by Hawk666 on 2010-06-24
yup i do get all that ill give that a try and get back to you thanks

---

### Post by Hawk666 on 2010-06-24
nailed it, thanks alot man, just had to correct a few inode errors, bitmaps, and blocks and i am back in business. just in time to i was gettin sick and tired of dealing with windows lol

---

### Post by rudy.b on 2010-06-24
Cool, glad to help.  :-)

---

