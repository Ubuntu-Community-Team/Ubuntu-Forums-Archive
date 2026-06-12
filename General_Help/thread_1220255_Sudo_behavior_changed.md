---
title: "Sudo behavior changed"
date: 2009-07-22
forum: General Help
---

### Post by jgull8502 on 2009-07-22
I recently upgraded from Intrepid to Jaunty. In Jaunty, I am experiencing some weird issues with "sudo." The first time I use sudo, I have to supply my password. However, it seems to persist for my entire session without ever having to enter my password again. This happens even across terminal sessions. For example, I can open a terminal, use sudo, close the terminal, then open a new terminal and not have to supply my password again. 

I'm hoping someone can help me go back to the old behavior where sudo times out after 15 minutes and across terminal sessions.

Below, I've posted /etc/sudoers which looks pretty standard to me.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

