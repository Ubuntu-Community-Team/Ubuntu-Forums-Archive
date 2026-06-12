---
title: "allow a user to run a single command as sudo?"
date: 2010-08-09
forum: General Help
---

### Post by pythonscript on 2010-08-09
Is there a way to set up a user account in the /etc/sudoers file so that it can run *onew* command as sudo, without a password, but only that command? (and it can't run any other commands, even as sudo with a password). Here's what I'm trying to do:

Have a user "admin" be able to run the adduser command, as sudo, without using a password, but not be able to run any other commands, even with the password, just like a normal user. Is this possible?

Thanks!

---

### Post by kerry_s on 2010-08-09
```
%admin ALL=NOPASSWD: /path/to/program
```

"%admin" can also be the name of the user instead, that way he does not have to be in the admin group.

i run several commands with no password.

---

### Post by garvinrick4 on 2010-08-10
```
gksudo gedit /etc/sudoers
```
Make line below look like this. If you want 30 minutes put in 30. If you want unlimited time use -1 make default line look like this below.



Defaults	env_reset,timestamp_timeout=-1


Here is mine: Using netbook here but the same.




#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset,timestamp_timeout=-1

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

