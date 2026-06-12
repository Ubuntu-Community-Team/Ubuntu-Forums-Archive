---
title: "grub - locking entries in menu.lst"
date: 2011-01-21
forum: General Help
---

### Post by RegUB on 2011-01-21
I have added the "password --md5 ...." directive before each of the "title" directives in my menu.lst, to prevent unauthorised people from adding/amending parameters on the kernel command line. This works fine.

However, if I select the first item in the list, it also requires the password to be entered before it will boot. I have tried changing the order of the entries, and it is always the first one which requires the password.

I know this behaviour can be forced by inclusion of a "lock" directive, but my menu.lst does not have this - so why is it requiring the password before it will boot?

---

