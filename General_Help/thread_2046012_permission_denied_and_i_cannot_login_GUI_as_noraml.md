---
title: "permission denied and i cannot login GUI as noraml user"
date: 2012-08-22
forum: General Help
---

### Post by NewUserFF on 2012-08-22
everything is nearly the same as the issue described:
[http://ubuntuforums.org/showthread.php?t=2036468]("http://ubuntuforums.org/showthread.php?t=2036468&page=2")

he didn't solve the problem, but only reinstall ubuntu 12.04. :(

i should add some: now i can login ubuntu 12.04 as root, but still doesnt work as a normal user.what's more, i can see "/usr/bin/python permission denied" when i type such command as "sudo ..." as a normal user. i guess maybe normal user cannot access "sudo" privilege. does anyone have some ideas?

```
id mycityofsky

uid=1000(mycityofsky) gid=1000(mycityofsky) groups=1000(mycityofsky),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)


``````


cat /etc/sudoers

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d


```each file seems fine

---

### Post by mzaam on 2012-08-22
try create new user with admin group,
may get different result

---

### Post by rukiaEnix on 2012-08-22
Try adding your user again, and add it to the sudoers file like this:

```

user    ALL=(ALL:ALL) ALL

```

Where user is obviously your user.

---

