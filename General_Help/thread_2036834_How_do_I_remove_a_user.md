---
title: "How do I remove a user"
date: 2012-08-03
forum: General Help
---

### Post by Hungry Man on 2012-08-03
I ran a adduser command and decided I'd like to remove that user. How do I do this?

edit: I just deleted the user folder, hope that works haha

---

### Post by steeldriver on 2012-08-03
that won't actually remove the user's entry from the password or group files - you should use 'deluser' (or the lower-level 'userdel') I think

man deluser

---

### Post by Paqman on 2012-08-03
Or the Users and Groups tool.

Note that neither will delete the users home folders by default, but you can add the --remove-home switch to deluser if you want to nuke them completely.

---

