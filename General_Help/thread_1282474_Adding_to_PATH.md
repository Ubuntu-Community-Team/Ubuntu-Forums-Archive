---
title: "Adding to PATH"
date: 2009-10-04
forum: General Help
---

### Post by iEthan on 2009-10-04
For some, reason, after aborting out of a Phusion Passenger install, I can't use sudo. I get this error:

```

Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
bash: sudo: command not found

```

How do I add to my PATH to add /usr/bin?

---

### Post by lswb on 2009-10-04
In a terminal 

```

PATH=$PATH:/usr/bin

```

However that will only be the path for that particular terminal session. The system default path is set a boot from the file /etc/environment. Normally all the bin and sbin directories are included.

an individual user path can also be set or modified in their ~/.profile ( or .bash_profile or .bash_login)

---

### Post by iEthan on 2009-10-04
Now it errors:

```

sudo: must be setuid root

```

---

### Post by lswb on 2009-10-04
Boot into recovery mode to get to a root shell, then 

chmod 4755 /usr/bin/sudo

Sounds like there may be other problems. Besides the aborted install, has anything else that might change any file permissions been done?

---

### Post by iEthan on 2009-10-04
No. I've fixed it. I went into Recovery Mode, Root Shell Access, and did the following:

```

chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

```

Then reboot.

---

