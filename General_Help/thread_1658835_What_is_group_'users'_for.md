---
title: "What is group 'users' for?"
date: 2011-01-03
forum: General Help
---

### Post by Pressurized on 2011-01-03
What is the group 'users' (gid 100) for?

It's tempting to use it as a general group for accounts that log in but would that cause a security risk?

I've done a search for files owned by this group and there don't appear to be any. Googling the words gives very non-specific results!

Cheers

---

### Post by wyliecoyoteuk on 2011-01-03
Usually a file will be owned by a particular user, but they are in the user group "users", so other members of that group may have read-only access.
Try right-clicking on a file in your home directory and viewing the permissions.

---

### Post by Pressurized on 2011-01-03
Thanks for the above but I'm actually quite comfortable with the ownership of files.

Perhaps I need to clarify my question.

Ubuntu creates a group 'users' with group ID 100 on installation that doesn't have any members. This could mean it's for something special like, for example, backup and shadow, but I cannot tell what.

```
#find / -group users
``` gives no results so does this imply that 'users' has no defined use and I could use it to add all my login accounts to so they could share files?

My Debian-based bubba servers seem to use it for just this purpose and it would be advantageous to do the same for commonality.

---

### Post by matt_symes on 2011-01-03
Hi

I think you can use the group for what ever you want. It just allows you a group to group all users together.

Here are some examples...

[http://ubuntuforums.org/showthread.php?t=1504765](http://ubuntuforums.org/showthread.php?t=1504765)

Kind regards

---

