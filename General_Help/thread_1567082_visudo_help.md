---
title: "visudo help?"
date: 2010-09-03
forum: General Help
---

### Post by SlugSlug on 2010-09-03
Hi All,

I am trying to allow one user to run a gksudo command with out a password being required.

I have edited visudo but it still prompts for password.

can anyone help?
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification
# Cmnd alias specification
# User privilege specification
root    ALL=(ALL) ALL
USERNAME ALL=(ALL) NOPASSWD: /usr/local/bin/APP.py
%sudo ALL=NOPASSWD: /usr/local/bin/APP.py
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```[FONT=Arial][SIZE=2]
[/SIZE][/FONT]

---

### Post by sisco311 on 2010-09-03
You have to add the **USERNAME ... NOPASSDW...** line at the end of the file or at least after the **%admin ALL=(ALL) ALL** entry:


```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification
# Cmnd alias specification
# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# USERNAME may run APP.py as another user without a password
USERNAME ALL=(ALL) NOPASSWD: /usr/local/bin/APP.py

```

where USERNAME is your login name.

Check out: [thread=1132821]HowTO: Sudoers Configuration[/thread]

> **ibuclaw said:**
> Sudo reads the sudoers file and applies permissions in order from top to bottom. So the last line in the file will overwrite any previous conflict with the config settings. So it is best to put new configuration lines at the bottom.

---

### Post by SlugSlug on 2010-09-03
Thank you

---

### Post by sisco311 on 2010-09-03
You're welcome!


Don't forget to mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

