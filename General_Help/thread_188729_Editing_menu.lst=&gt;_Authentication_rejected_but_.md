---
title: "Editing menu.lst=&gt; Authentication rejected but able to edit anyway ?"
date: 2006-06-04
forum: General Help
---

### Post by Browser_ice on 2006-06-04
I wanted to re-edit my mutiple boot config as it added new sessions and therefore the default one wasn't the same as before. So I started Terminal and went to edit my menu.lst

It gave me an authentication error message but I was able to edit/save it anyway.

**Why **????

[B][INDENT]#########@Linux:~$ gksudo gedit /boot/grub/menu.lst
(gedit:8907): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/INDENT][/B]

---

### Post by gatti on 2006-06-04
I get the same message but only if I log in as one of the other users on the system who is allowed to "execute system administration tasks". As you say it works anyway so I just ignore it.

---

### Post by givré on 2006-06-04
Ignore it, it is just a warning

---

