---
title: "&quot;evolution-backup&quot; process hangs"
date: 2012-02-05
forum: General Help
---

### Post by rhill on 2012-02-05
I found here somewhere that evolution-backup can be used to backup evolution data from the command line. Example:

/usr/lib/evolution/2.30/evolution-backup --backup "Ubuntu One/evolution-backup.tar.gz"

It works fine, the tar file is created. However, the process hangs afterward, I need to control-C it to force evolution-backup to quit. This means I can't use this command in a shell script.

Any idea why it hangs and how to prevent this? Or a workaround I could use in a shell script?

Edit: Here is the output from the command, after which it hangs forever:

Evolution process exited normally
** Message: evolution --quit
EI: MAIL PREFS** Message: rm /home/me/.evolution/.running
rm: cannot remove `/home/me/.evolution/.running': No such file or directory
** Message: gconftool-2 --dump /apps/evolution > /home/me/.evolution/backup-restore-gconf.xml
** Message: cd /home/me && tar chf - .evolution .camel_certs | gzip > 'Ubuntu One/evolution-backup.tar.gz'

---

### Post by dcstar on 2012-02-06
> **rhill said:**
> I found here somewhere that evolution-backup can be used to backup evolution data from the command line. Example:

/usr/lib/evolution/2.30/evolution-backup --backup "Ubuntu One/evolution-backup.tar.gz"

It works fine, the tar file is created. However, the process hangs afterward, I need to control-C it to force evolution-backup to quit. This means I can't use this command in a shell script.

Any idea why it hangs and how to prevent this? Or a workaround I could use in a shell script?

Edit: Here is the output from the command, after which it hangs forever:

Evolution process exited normally
** Message: evolution --quit
EI: MAIL PREFS** Message: rm /home/me/.evolution/.running
rm: cannot remove `/home/me/.evolution/.running': No such file or directory
** Message: **gconftool-2 **--dump /apps/evolution > /home/me/.evolution/backup-restore-gconf.xml
** Message: cd /home/me && tar chf - .evolution .camel_certs | gzip > 'Ubuntu One/evolution-backup.tar.gz'

This script is obviously using Gnome 2 components, Gnome 2 stuff is not installed by default in Ubuntu 11.10 and later.

You may need to verify that all the bits the backup script is expecting are actually installed on your system.

---

