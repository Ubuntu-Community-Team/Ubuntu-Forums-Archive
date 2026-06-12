---
title: "broke my sudo"
date: 2009-09-19
forum: General Help
---

### Post by gwydionwaters on 2009-09-19
i reinstalled 8.10 and i used the option to allow root login during install which appears to have left out any entries for my regular user account in the sudoers file, so i can't do things like set administration options via the gui unless i log in as root. i can't even add items to my menu without this so it seems. i just want the default settings that work. could someone post their sudoers file? you can replace sensitive things with <item type> if you want. thanks for reading :)

---

### Post by sisco311 on 2009-09-19
the default sudoers file:
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

just add your user to the admin group:
```
gpasswd -a username admin
```

But, if you want, you can change the authentication mode to su and use the root password to run admin tasks.

gksu:
```
gksu-properties
```

PolicyKit:
edit the /etc/PolicyKit/PolicyKit.conf to:
```
<config version="0.1">
</config>

```

NOTE: **backup the file before editing!!!**

```
cp /etc/PolicyKit/PolicyKit.conf /etc/PolicyKit/PolicyKit.conf.old
```

---

### Post by earthpigg on 2009-09-19
```
chris@chris-vm:/etc$ sudo cat sudoers
[sudo] password for chris: 
# /etc/sudoers
#
# ***_This file MUST be edited with the 'visudo' command as root._***
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
chris@chris-vm:/etc$
```

---

### Post by gwydionwaters on 2009-09-19
awesome thanks! that did the trick

---

