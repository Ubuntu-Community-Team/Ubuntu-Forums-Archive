---
title: "Anybody else having issues with downloading pubkeys?"
date: 2010-05-02
forum: General Help
---

### Post by inameiname on 2010-05-02
In the past 24 hours or so I can't seem to download pubkeys very well, and I'm not sure why. 

As always, I just use the following format:

gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -


....works like a charm......that is up until today for some reason.

Now, after several minutes, it does seem to finally do so, but I'm just curious is there something up with the service.

---

### Post by inameiname on 2010-05-02
Nevermind. It's working now. I guess it was just the ubuntu servers or something that was keeping it extremely slow.

---

