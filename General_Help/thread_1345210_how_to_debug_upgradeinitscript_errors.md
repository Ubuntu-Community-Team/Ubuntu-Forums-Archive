---
title: "how to debug upgrade/initscript errors"
date: 2009-12-03
forum: General Help
---

### Post by jmarks on 2009-12-03
I recently upgraded to 64-bit 9.10 from 9.04. However, the samba and winbind upgrades keep throwing errors, where the initscript "start" command fails. I would be happy to post log files if someone could tell me which ones to post. 
The error text is: 
```
Setting up samba (2:3.4.0-3ubuntu5.1) ...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up winbind (2:3.4.0-3ubuntu5.1) ...
 * Starting the Winbind daemon winbind                                   [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (2:3.4.0-3ubuntu5.1) ...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up winbind (2:3.4.0-3ubuntu5.1) ...
 * Starting the Winbind daemon winbind                                   [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
 winbind

```
Thanks in advance for any help!

---

