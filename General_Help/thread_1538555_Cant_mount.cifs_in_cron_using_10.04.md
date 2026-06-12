---
title: "Cant mount.cifs in cron using 10.04"
date: 2010-07-25
forum: General Help
---

### Post by craigrose on 2010-07-25
Hi

This 

/sbin/mount.cifs //<remote host>/<folder> /mnt/<mount point> -o credentials=/opt/administrator/credentials

 works fine from a root command prompt and using sudo.  The credentials file is read and the share mounts.  There is no prompt for password.

However it will not work from cron.  It prompts for a password and fails to mount with the following error:

```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```My credentials file has no spaces in it and no empty lines (including at the end). 

/opt/administrator/credentials:

```
username=<username>
password=<secret>
```I have search many forums and tried many commands - always the same!  I originally used:

```
mount -t cifs ......
``` but that was worse.  It couldn't even find the mount.cifs helper.

I also set it up in fstab and tried ```
mount  /mnt/<mount point>
```  This worked from the command line but not from cron.

Can anyone help?

Craig

---

### Post by craigrose on 2010-07-26
Thinking some more on this if it is permissions then perhaps I need to check the permissions on each path used in the command.

These are:

/sbin/mount.cifs 
//<remote host>/<folder> 
/mnt/<mount  point>
/opt/administrator/credentials

Are there any hidden ones I missed, configuration files perhaps for mount.cifs

Any way I will check the permissions on each and report back here.

EDIT: Ah!  Plus the permissions that cron runs with

---

