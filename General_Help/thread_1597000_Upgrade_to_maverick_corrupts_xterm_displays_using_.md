---
title: "Upgrade to maverick corrupts xterm displays using nvidia"
date: 2010-10-14
forum: General Help
---

### Post by mbeierl on 2010-10-14
I used to have this problem a long time ago and thought it was long gone, but thanks to Maverick, a trip down memory lane is in order.  With compiz enabled on nvidia, I get vertical bars in all my xterms making using my computer now nearly impossible.

I've attached a shot of what it looks like.  Please, anyone, if you've been bitten by this and know of a way out, I'd love to hear from you.

---

### Post by Zaff on 2010-10-16
I have the same problem.
It seems to be related to compiz because xterm is fine when changing the window manager back to metacity.

just found this bug report : [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258)

---

### Post by mbeierl on 2010-10-18
WOOT!  The patched compiz binary attached to that bug report fixes the problem for me.  Thank you so much for finding that report!  I'd tried using different search terms and had been unsuccessful so far.

Btw, this is the first time in a long time that I've received a response in the forums, so a second thank you for restoring my faith in the community!

---

