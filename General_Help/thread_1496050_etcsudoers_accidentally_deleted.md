---
title: "/etc/sudoers accidentally deleted"
date: 2010-05-28
forum: General Help
---

### Post by mpetrovic on 2010-05-28
Hello,

Thanks to my early hours stupidity :) I have accidentally deleted the contents of sudoers file (while trying to add a line through CLI).

Anyway, I'm still logged in and can please someone paste me the default contents of the sudoers file on Lucid Lynx?

Thanks a lot!!! :)

---

### Post by Woody1987 on 2010-05-28
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

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by WorMzy on 2010-05-28
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

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

There you go. :)

---

### Post by mpetrovic on 2010-05-28
Thank you both very much! :)

---

