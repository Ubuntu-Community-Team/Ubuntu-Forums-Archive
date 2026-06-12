---
title: "apt-mirror is already running , exiting at /usr/bin/apt-mirror line 187."
date: 2010-01-07
forum: General Help
---

### Post by Stephen Lilley on 2010-01-07
Bug #424462 this bug is already discussed on [https://bugs.launchpad.net/ubuntu/+source/apt-mirror/+bug/424462](https://bugs.launchpad.net/ubuntu/+source/apt-mirror/+bug/424462)

it has given the following solution 
"the case for this error message is that file:
/var/spool/apt-mirror/var/apt-mirror.lock
was not deleted on apt-mirror exit.
If you delete apt-mirror.lock file, then apt-mirror will run OK, but you have to delete the file every time apt-mirror finishes it's job."

I went to this location in karmic and couldn't find apt'mirror.lock in order to delete it :icon_frown:. At the moment I can't use apt-mirror because it thinks it is already running. 

Anyone with suggestion on how I might fix this.

---

### Post by Stephen Lilley on 2010-01-08
I tried the un-install and reinstall using synapitc but I get the same error. Any suggestions about what I might do to change this. Remembering there isn't any file at /var/spool/apt-mirror/var/apt-mirror.lock

---

### Post by Stephen Lilley on 2010-01-09
A friend of mine solved my problem I had changed the /var directory in the mirror script and the offending file was there. I deleted and now I can use the mirror script and mirror a repository

---

### Post by AlexDBall on 2010-01-21
Glad you found the solution for this. I have the exact same problem and cannot find the way out of it.

Please set the status of this thread as "Solved"

---

### Post by morchuboo on 2010-06-15
I know this is an old post but it still shows in google searches.
Moving the lock file location does not solve the issue.
The issue is caused by a bug in how the apt-mirror script handles SIGINT SIGHUP and SIGTERM signals caused by either Ctrl-Cing to terminate or when the script fails due to not being able to find the repositories (incorrect repository or dns resolution errors).
The use of a lock file was introduced in 0.4.6 and a patch submitted for 0.4.7. It seems the patch only partly fixed it and a further patch is in the works.

For now, it is best to remove the lockfile if the script fails and wait for a new patch. 
See the bug report:[https://bugs.launchpad.net/ubuntu/+source/apt-mirror/+bug/424462]("https://bugs.launchpad.net/ubuntu/+source/apt-mirror/+bug/424462")

---

### Post by eckertd on 2013-03-27
I know this is an OLD thread, but I was just running into the same issue in Quantal.

flock() on closed filehandle LOCK_FILE at /usr/bin/apt-mirror line 194.
apt-mirror is already running, exiting at /usr/bin/apt-mirror line 197.

Appearing in the cron log, and interactively when attempting to run as 'apt-mirror' user.  However, <var_path>/apt-mirror.lock did not exist.  It would run to successful completion as the 'root' user, however.

The repository path was created by 'root' and the first run of apt-mirror was performed as 'root' as well.  The Perl script only reports that it can't create the lock file, and the message seems to indicate that the lock file already exists.  However, in my case the lock file couldn't be created due to the 'apt-mirror' user not having write privs.

chown -R apt-mirror:apt-mirror <repository-path>

It now runs to successful completion as 'apt-mirror'.  Perhaps the $lock value within the lock_aptmirror function can be further scrutinized to yield a more informative error message.

---

