---
title: "Changing ID of my login account"
date: 2005-01-23
forum: General Help
---

### Post by nhaughton on 2005-01-23
I want to change the ID of my login account, so it matches the account on another machine running a different distro (so I can share a mounted folder across distros). In Ubuntu I have altered /etc/passwd  and /etc/group, but this doesn't let me login using the account. What else do I have to do? My other distro is RH based, and apparently there is more to this question in a Debian distro.

Neil Haughton

---

### Post by mendicant on 2005-01-23
I've done this in a Debian system, and it's just what you did, plus log out and log in again (or ssh in from an existing login).  Ubuntu should be the same.

---

### Post by nhaughton on 2005-01-24
I did that, but it doesn't work - I can't login again.

Here are my /etc/passwd and /etc/group files (just the relevant lines)  from both distros:

Mandrake (works):

/etc/passwd:
neil:x:501:501:neil:/home/neil:/bin/bash

/etc/group:
neil:x:501:

Ubuntu (doesn't work)

/etc/passwd:
neil:x:501:501:neil::/home/neil:/bin/bash

/etc/group:
neil:x:501:

After changing Ubuntu to the above, I also (under Ubuntu, as root) did a chown -R neil:neil /home/neil, then logged out and tried to log in again. Gnome had 'lost' my neil account from the graphical login screen, and would not let me log in as 'neil' at all.

When I altered the Ubuntu files back to the original userID (1000) and re-chowned my home directory accordingly it worked again, although the graphical User and Groups application doesn't load now. Now I'm kinda stuck on this.

Can anyone help?

---

