---
title: "I need the root passw"
date: 2010-09-18
forum: General Help
---

### Post by Argentino on 2010-09-18
Hi Guys,

I want to install a Lexmark printer which for some crazy reason wants the root password.

The deb installer will not take my password which has sudo privileges.

I understand that Ubuntu locks the root pass, but how can I get around this?

Thanks!

- Pablo

---

### Post by CharlesA on 2010-09-18
You really shouldn't enable the root account.

What happens if you do this:

```
sudo dpkg -i /path/to/deb.deb
```

---

