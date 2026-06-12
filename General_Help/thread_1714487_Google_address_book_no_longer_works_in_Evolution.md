---
title: "Google address book no longer works in Evolution"
date: 2011-03-25
forum: General Help
---

### Post by apochry on 2011-03-25
Hi,

I'm using Evolution with Google Address Book and it was working perfectly until several days ago.  Suddenly I begun to get the following error message:

[IMG]http://img835.imageshack.us/img835/2447/evolutionerror.png[/IMG]

I did some research in the forums and the only thread I found is about two years ago and it was not solved. pupfishdesign reports [there]("http://ubuntuforums.org/showthread.php?t=1107244") to have the exact same issue as me. Like him I didn't change any Google password, deleting passwords from the Ubuntu keyring and re-entering them when prompted in Evolution didn't help me also.

So, it would be nice, if someone shares some experience or gives me a hint how to solve the problem.

Thanks!

Izzo

---

### Post by apochry on 2011-03-27
After updating Evolution from 2.30.2 to 2.32.2 the error message looks a bit different:

[IMG]http://img848.imageshack.us/img848/1415/evoerror.png[/IMG]

I don't use any proxies for Gmail and my account name and pass are right...
Any ideas?

---

### Post by apochry on 2011-03-27
I solved it!

Referring to Josh's post  in [_this_]("http://ubuntuforums.org/showthread.php?p=10607394#post10607394") thread I changed the Proxy Setting in the 'Network Preferences'-tab from "Use system defaults" to "Direct Connection to the Internet" and restarted Evolution. This also fixed the problem I had with loading massage images.

Thanks Josh!

---

