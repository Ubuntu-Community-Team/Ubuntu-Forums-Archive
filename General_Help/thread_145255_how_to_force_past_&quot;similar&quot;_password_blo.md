---
title: "how to force past &quot;similar&quot; password block?"
date: 2006-03-15
forum: General Help
---

### Post by ChrisC on 2006-03-15
I'd like to change my password.  When I tried to do so (either via GUI or CLI), it said that the new password was too similar to the old one.  I really don't care -- change the damn password please! :)

So, I would like to force the password change.  I asked on #ubuntu (IRC) and that got me on the trail of /etc/pam.d/passwd .  In there was just one active line that read:

   @include common-password

and in the /etc/pam.d/common-password file was just this line:

   password   required   pam_unix.so nullok obscure min=4 max=8 md5

I can't find any further docs.  What do I do exactly to suppress the password similarity checking?

---

### Post by ChrisC on 2006-03-16
Anyone?

---

### Post by halfvolle melk on 2006-03-16
Can't you just change it to something entirely different and then change it to the "too similar" one? this (bad practice no doubt) has worked for me.

---

### Post by Ivan Matveich on 2006-03-16
sudo passwd $your_username

---

### Post by ChrisC on 2006-03-16
[QUOTE=Ivan Matveich]sudo passwd $your_username[/QUOTE]

Thanks, Ivan, that worked!  How simple.  I guess when invoked as the superuser, it bypasses the usual rules.

HM, the reason I didn't want to try your suggestion was because I didn't know how far back it remembered old passwords (1 password back?  2?  50?) and envisioned getting stuck with a "temporary" password.

This should go into the FAQ/guide ... particularly because the new password was not at all similar; there happened to be 3 letters of overlap, but they were two completely different words ... like "computer" and "priceless".

---

