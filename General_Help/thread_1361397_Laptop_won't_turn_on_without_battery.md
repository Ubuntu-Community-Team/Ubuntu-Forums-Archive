---
title: "Laptop won't turn on without battery"
date: 2009-12-21
forum: General Help
---

### Post by hinhey on 2009-12-21
Hey all, 

Starting a month ago, my laptop refused to turn on with the power cord plugged in. Whenever I try, it says

```
root filesystem is currently mounted in read-only mode
A maintenance shell will now be started
After performing system maintenance press CONTROL-D to terminate the shell and restart the system
Give root password for maintenance 
(or type Control-D to continue)
```

I've tried my sudo password with no luck. Any ideas?

Thanks,
hinhey

---

### Post by stew721 on 2009-12-22
> **hinhey said:**
> I've tried my sudo password with no luck. Any ideas?
The password used for sudo is the password of the user account.  You need to use the password of the actual "root" account.

---

### Post by Mark Phelps on 2009-12-22
> **stew721 said:**
> The password used for sudo is the password of the user account.  You need to use the password of the actual "root" account.

Huh??  On a single-user default setup, the user's password IS the root password -- unless you go to the trouble to specifically change it.

Besides, what does this have to do with the laptop needing the battery in order to turn on?

---

### Post by stew721 on 2009-12-22
> **Mark Phelps said:**
> Huh??  On a single-user default setup, the user's password IS the root password -- unless you go to the trouble to specifically change it.

Besides, what does this have to do with the laptop needing the battery in order to turn on?
If a root password wasn't set, then just press ENTER at the password prompt.  Otherwise, enter the root password.  If the root password has been forgotten, that can be fixed as well.  It's been awhile, but if I remember correctly:

[LIST=1]
[*]Restart the computer.
[*]Edit GRUB and boot.
[*]Remount as needed.
[*]Remove or reset the root password.
[*]Flush file system buffers.
[*]Restart the computer.
[/LIST]
Other than that, my post didn't address any part of theirs other than that which was quoted within mine.

---

