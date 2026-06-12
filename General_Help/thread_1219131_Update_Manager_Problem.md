---
title: "Update Manager Problem"
date: 2009-07-21
forum: General Help
---

### Post by Quarkrad on 2009-07-21
Running 9.04.  Every time update manager runs following message pops up:
[B]
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F[/B]

do I have to do anything to stop this happening/correcting the problem?

---

### Post by philcamlin on 2009-07-21
omk its firefox update thats the issue

do this first though 

sudo apt-get remove firefox

then follow this 

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

follow that to correct it

---

### Post by Quarkrad on 2009-07-23
Sorted -  thanks.

---

