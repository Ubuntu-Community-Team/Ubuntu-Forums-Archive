---
title: "Tor/Vidalia broken on update (thanks guys)"
date: 2012-01-17
forum: General Help
---

### Post by Cadeyrn on 2012-01-17
I noticed new versions of Tor and Vidalia in the repository, so I updated them. Now Vidalia is acting as if it was never properly installed on top of tor (and tor is acting the same, because it's launching on boot), and when I run it, it says /var/run/tor must be owned by the user. I tried chown-ing it to me, but then it said the directory permissions are too permissive. I've tried every variant of permissions imaginable, and it never stops saying that.

So, I tried dpkg-reconfigure and dpkg --reconfigure on Vidalia. Neither one works. dpkg-reconfigure simply refuses to ask me the debconf user-set questions again, no matter what flags I set. I've also tried using Synaptic to "completely remove" and then install. If I could just reinstall Vidalia in some way that lets me tell it to take over Tor (the setting I had previously), this whole mess could be fixed.

---

