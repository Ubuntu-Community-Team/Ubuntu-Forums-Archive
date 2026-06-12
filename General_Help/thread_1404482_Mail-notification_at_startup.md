---
title: "Mail-notification at startup"
date: 2010-02-11
forum: General Help
---

### Post by venicequeen7706 on 2010-02-11
Hi I'm trying to get mail-notification to run at startup. I tried adding it to startup applications under system > preferences using the same command I use to start it from terminal and that doesn't seem to be working.

---

### Post by ankspo71 on 2010-02-11
Hi,
Try going back to the Startup Applications list and see if it is still listed in there. Ubuntu 9.10 had a known minor bug (when I last used it), that caused the startup applications list not to save entries on the first try. A work around for this is to create the entry as normal, but before you exit the list, click on the edit button a few times to make sure it stays. Then you can exit the list, then check again to be sure, before restarting the computer. 
Hope this helps.

---

### Post by venicequeen7706 on 2010-02-11
> **ankspo71 said:**
> Hi,
Try going back to the Startup Applications list and see if it is still listed in there. Ubuntu 9.10 had a known minor bug (when I last used it), that caused the startup applications list not to save entries on the first try. A work around for this is to create the entry as normal, but before you exit the list, click on the edit button a few times to make sure it stays. Then you can exit the list, then check again to be sure, before restarting the computer. 
Hope this helps.
it is listed.

---

### Post by JackRock on 2010-02-11
I have a similar issue with CheckGmail.  I have it listed in the Startup applications, and it does not work.  It's pinned to the panel, so I know the string I used works...it's just not being done automatically at startup.

---

### Post by crlang13 on 2010-02-11
i'm using mail notification on ubuntu 9.10, no problems there

---

### Post by venicequeen7706 on 2010-02-11
> **crlang13 said:**
> i'm using mail notification on ubuntu 9.10, no problems there
thats what i'm running too. How did you set it up to run automatically on startup?

---

### Post by crlang13 on 2010-02-11
> **venicequeen7706 said:**
> thats what i'm running too. How did you set it up to run automatically on startup?

hmmmm, sorry buddy, I didn't read your original post closely enough:oops: - i thought you were on a different one and was trying to recommend another mine! oops...

All I had to do was install it through the software center, go to system > preferences > startup apps and add the new app with the command usr/bin/mail-notification

is that the command you're using?

---

### Post by venicequeen7706 on 2010-02-12
> **crlang13 said:**
> hmmmm, sorry buddy, I didn't read your original post closely enough:oops: - i thought you were on a different one and was trying to recommend another mine! oops...

All I had to do was install it through the software center, go to system > preferences > startup apps and add the new app with the command usr/bin/mail-notification

is that the command you're using?
no problem. I have been using the command 'mail-notification' because that alone runs it from the terminal. I tried usr/bin/mail-notification but that doesn't seem to be working either.

---

### Post by venicequeen7706 on 2010-02-13
I played around and figured out if i make it /usr/bin/mail-notification it works so thank you very much for the help

---

