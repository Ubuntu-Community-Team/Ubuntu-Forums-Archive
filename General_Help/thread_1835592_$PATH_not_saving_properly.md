---
title: "$PATH not saving properly"
date: 2011-08-29
forum: General Help
---

### Post by [V] on 2011-08-29
I have a directory saved in my $PATH variable via the ~/.bashrc file.
It works fine when I physically use my box.

When I SSH into my box using the same login, my $PATH variable is no longer saved.
What am I missing here?

Thanks

---

### Post by [V] on 2011-08-30
anyone?

---

### Post by Sazhen86 on 2011-08-30
.bashrc isn't sourced when logging in via ssh as it not sourced by bash when it is invoked as a login shell.  The best way to ensure it is used is to source it at the end of .bash_profile with something like:

if [ -f ~/.bashrc ]; then
  . ~/.bashrc
fi

---

