---
title: "sudo: must be setuid root??"
date: 2010-08-01
forum: General Help
---

### Post by CoolJohnB on 2010-08-01
[B]I recently changed the ownership of a HD partition since then update manager doesn't work If I click any button it is busy for a short time and goes back to normal also it doesn't ask for a password.

If I try to update using Terminal I get this message: sudo: must be setuid root

It also doesn't ask for a password, not sure what I've done! But can anyone help me put it right?

Thanks for any help offered.
[/B]

---

### Post by Bachstelze on 2010-08-01
You seem to have messed up your permissions, you'll probably have to reinstall.

To make sudo setuid root, you can do

```
chmod +s /usr/bin/sudo
```

from recovery mode, but you'll probably have a lot of other issues.

---

### Post by mcduck on 2010-08-01
That sounds like you have changed the ownership/permissions of the system directories. That's not going to work, much of the system stuff requires certain ownership and permissions to work.

Sadly, that's not something you could easily recover from. While you could try to get a list of correct permissions and ownerships for each individual file it would be insanely lot of work (the only time I've seen anybody do that took a week's work). So you'll probably just have to reinstall. And leave the system directories alone this time, if you need to access system stuff you change your permissions (by using "sudo"), not the file/directory permissions. :)

---

