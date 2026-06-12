---
title: "apt-get problem Setting up setiathome (3.08-4)"
date: 2006-02-16
forum: General Help
---

### Post by foolsh on 2006-02-16
hi i wasn't sure where to post this so here goes

the problem comes from when i was trying to install setiathome (3.08-4) from synaptic
 the progress stops at
```
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--09:21:45--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
           => `/tmp/filePHqWlc'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...
Retrying.

--09:26:55--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 2) => `/tmp/filePHqWlc'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...

```
killing the dpkg and synaptic processes and running
#dpkg --configure -a
results in the same error i assume that alien.ssl.berkeley.edu is down or no longer exists

My question is how do i undo what apt-get is doing and cut my losses
or to rephase that how do tell apt-get to ignore the unconfigured package?

---

