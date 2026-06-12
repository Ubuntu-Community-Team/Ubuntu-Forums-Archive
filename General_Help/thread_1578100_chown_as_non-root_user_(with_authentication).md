---
title: "chown as non-root user (with authentication)"
date: 2010-09-19
forum: General Help
---

### Post by rsanden on 2010-09-19
I am currently responsible for administering a shared Ubuntu machine with several unrelated users. Some of these users own multiple accounts and would like to "chown" files between them. Currently, I must handle such requests manually, and this is inconvenient.

I am looking for a way to allow non-root users to chown files with authentication (i.e. prompt for the password of the user to which ownership is being set to). This would prevent an exploit such as:

> cp /bin/bash ~/sudobash
chmod 4777 ~/sudobash
chown root:root ~/sudobashDoes such a solution exist?

---

### Post by hawthornso23 on 2010-09-20
Suppose your users want to switch a file belonging to USER2 to ownership by USER1. Why doesn't USER1 just make a copy of the file. The copy will belong to USER1. USER2 can then delete the original if it is no longer needed.

---

### Post by QLee on 2010-09-20
[QUOTE=rsanden]...
I am looking for a way to allow non-root users to chown files with authentication (i.e. prompt for the password of the user to which ownership is being set to). [/QUOTE]
Huh?
You want the users to all have access to each others passwords? Not a very useful security model. They might as well all logon as the same user and then have access to the files.

---

