---
title: "/usr/local/etc/sudoers is mode 0444, should be 0440"
date: 2011-11-05
forum: General Help
---

### Post by orz_woo on 2011-11-05
I don't fully understand this.
I know the solution is get into recovery mode and run chmod 440 /etc/sudoers

Isn't mode 0444 got more permission?
How come if /etc/sudoers isn't mode 0440 then when doing sudo will get an error.

---

### Post by lechien73 on 2011-11-05
Because you are correct that 444 has more permissions than 440. The sudoers file requires that just the file's owner and those in the same group can read it. When you change the mode to 444, then the file can be read by everyone. That's why sudo won't work if the permissions are too lax.

The way to correct it is, as you say, to boot into recovery mode and set the right permissions.

---

