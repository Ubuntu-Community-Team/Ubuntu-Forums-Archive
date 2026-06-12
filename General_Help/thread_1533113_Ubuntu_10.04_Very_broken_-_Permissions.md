---
title: "Ubuntu 10.04 Very broken - Permissions?"
date: 2010-07-17
forum: General Help
---

### Post by naxtek on 2010-07-17
Hi,

I'm having some real troubles with my install of Ubuntu 10.04 LTS.

It was a fresh install just after 10.04 was released, so it's not been installed long.

Just recently lots of things have stopped working

[LIST]
[*]I can't sudo (sudo: must be setuid root)
[*]Trying to su root tells me I got the password wrong, even though I know it's right
[*]Sound has broken
[*]Brasero won't write CDs anymore
[*]Plugging in a pendrive gives some permissions mounting error
[*]Clicking 'shut down' just logs out.  The machine won't shut down at all.
[/LIST]
I'm guessing this might all be related to permissions/users?  I really don't want to have to reinstall again!  Any help appreciated...

---

### Post by sisco311 on 2010-07-17
To fix the sudo issue, boot into recovery mode and set the correct permissions on the file:
```
chown root: /usr/bin/sudo
chmod 4111 /usr/bin/sudo
```

You may have to hold down the Shift key during the bootup in order the boot menu to show up.

---

