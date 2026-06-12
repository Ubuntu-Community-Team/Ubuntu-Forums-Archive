---
title: "How to restore a user directory from a compressed file on login?"
date: 2012-05-12
forum: General Help
---

### Post by GeoMX on 2012-05-12
I'm updating to 12.04 from 10.04.
On Ubuntu 10.04, I used to delete myuser directory and restore it from a gzipped file, I did so by using scripts in /etc/gdm/.

On Ubuntu 12.04, I've found I can indicate a script to run on login by setting the session-setup-script in lightdm.conf, however, trying to run this script:
```
#!/bin/sh

rm --recursive --force /home/myuser
tar -xpPzf /home/myuser.tar.gz -C /home/

```
does not allow the sessiont to start: after entering myuser password, the screen goes black and then back to lightdm greeter, it happens for every user, not only myuser.

Placing the same instructions in the cleanup (session-cleanup-script) works fine, but I need to run it when logging in, though.

Any advice?

---

