---
title: "Changing UID's"
date: 2004-10-23
forum: General Help
---

### Post by devscott on 2004-10-23
What is the proper way for Changing UID's for users.

Why?

The linux server has a differ uid for my account than my ubuntu box. ( I'm loving the current release.)  I want to access my home directory via nfs, but uid's need to be the same. 

Any help would be great. Thank you to all in advance.

---

### Post by jmings on 2004-10-23
On my server (running SimplyMEPIS 2004.03) on a terminal I type:
$ id
uid=1000(wizard) .......
$
On the Ubuntu system I use:
[Applications] [System Tools] [Root Terminal]
and enter the password when prompted.  Now in the root terminal:

root@casandra:/home/wizard # cd /etc
#  Look for my user name in the password file
root@casandra:/etc # grep wizard passwd
wizard:x:1001:1000:Jerry Spencer Mings,,,:/home/wizard:/bin/bash
# the 3rd field is my current uid - 1001
# make sure there are no users with a UID of 1000
root@casandra:/etc # grep :1000: passwd
wizard:x:1001:1000:Jerry Spencer Mings,,,:/home/wizard:/bin/bash
# edit the password file
root@casandra:/etc # gedit /etc/passwd
# ignore the warning
(gedit:4760): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

# use the gedit window to change :1001:1000: to :1000:1000:
# verify it...
root@casandra:/etc # grep :1000: passwd
wizard:x:1000:1000:Jerry Spencer Mings,,,:/home/wizard:/bin/bash
# go the home directory
root@casandra:/etc # cd ~wizard
# Recursivly change the ownership of all my $HOME files to wizard (the new uid)
root@casandra:/home/wizard # chown -R wizard  ~wizard
root@casandra:/home/wizard # ls -ld .
drwxr-xr-x   14 wizard   wizard        688 2004-10-23 18:42 .
root@casandra:/home/wizard #

---

