---
title: "Prevent Evolution from always asking for passwords"
date: 2010-12-13
forum: General Help
---

### Post by grojo on 2010-12-13
Hi,

after trying everything out from various posts I found a solution to prevent Evolution from prompting for passwords over and over again when I sent/receive emails. As I guess I'm not the only one concerned, I post here a reply I did for another thread.

The problem came from Seahorse, which had a default keyring folder I  couldn't delete. I think Evolution used that folder, although another  one ('login' in my case) was ticked as 'default'.

**Solution:**
- delete all Evolution password entries in Seahorse (*Application/accessories/Passwords and Encryption keys*): expand the login folder (or the one you have the Evolution pwd in) and delete them.
- open *~/.gnome2/keyrings/* folder. You should have there a **default.keyring** file (or something similar), along maybe a **login.keyring **and so on. The **default.keyring **file is the one to get rid of.

```
sudo rm ~/.gnome2/keyrings/default.keyring
```- check in Seahorse that the default folder has gone.
- open Evolution and you should from now have to retype your password only once.

Voila. I hope it helps.

---

