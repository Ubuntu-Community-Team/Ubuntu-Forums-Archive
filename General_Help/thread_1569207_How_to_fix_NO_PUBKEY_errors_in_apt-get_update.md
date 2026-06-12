---
title: "How to fix NO_PUBKEY errors in apt-get update"
date: 2010-09-06
forum: General Help
---

### Post by JohnHeikkila on 2010-09-06
Okay, here's a fix to an error you might get when doing apt-get update.

Let's say you have this error:
```
W: GPG error: http://ftp.de.debian.org stable/non-US Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: You may want to run apt-get update to correct these problems
```
And apt-get update doesn't help (obviously?).

Here's the fix:

[B]1.
```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9AA38DCD55BE302B
``` depending on the key you get the error on, switch the *9AA38DCD55BE302B* to the key you need to get.[/B]
[B]2.
```
gpg --export --armor 9AA38DCD55BE302B | sudo apt-key add -
```
Once again, switch the *9AA38DCD55BE302B* to whatever necessary.[/B]
**3. You should be [COLOR="Lime"]done[/COLOR]! Run *apt-get update* to check!**

---

