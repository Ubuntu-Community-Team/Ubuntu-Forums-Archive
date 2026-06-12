---
title: "USC Amnesia - Error 401 unauthorized"
date: 2012-06-06
forum: General Help
---

### Post by Carborundum on 2012-06-06
While performing a routine system update today, my Update Manager threw a strange error:

```
W: Failed to fetch  https://private-ppa.launchpad.net/commercial-ppa-uploaders/amnesia/ubuntu/dists/precise/main/binary-i386/Packages   The requested URL returned error: 401
```So for whatever reason, I'm not authorized to access the private-ppa for my copy of Amnesia, purchased through the HIB V.

Even though it's just a cosmetic issue (as Update Manager thrown an ugly error message every time it runs (it still works though)), I would very much like to fix it. Any ideas?

---

### Post by Carborundum on 2012-06-07
I looked at /etc/apt/auth.conf, where the credentials for purchased software is stored, to see if I could log in to the ppa manually. It worked for Swords&Sworcery and Limbo (both also purchased through the HIB V and added at the same time in the same way), but not for Amnesia.

Looks like it's a problem on Canonical's end, then. I'll give them some time to see if the problem goes away by itself (I imagine they have their hands full with HIB related stuff at the moment). If not, I'll contact [EMAIL="pay-support@canonical.com"]pay-support@canonical.com[/EMAIL].

Edit: In the mean time, I have unchecked that specific ppa in Synaptic, so now Update Manager doesn't complain anymore.

---

