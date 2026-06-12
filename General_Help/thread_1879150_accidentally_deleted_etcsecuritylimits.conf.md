---
title: "accidentally deleted /etc/security/limits.conf"
date: 2011-11-11
forum: General Help
---

### Post by troubledone on 2011-11-11
Later, by looking it up, I guess I found out that it's purpose was to set limits on how many processes could be running at once.  I guess that means it's important.  How do I get another copy, if I can?

---

### Post by Elfy on 2011-11-11
Mine looks like
```

# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file

```

You could try recreating it 

using gedit, Alt+F2
```
gksudo gedit /etc/security/limits.conf
```

and copying that in - but I don't know if your file said anything?

When you say you deleted it - did you use rm in a terminal or did you do it in a root nautilus - if you did it in a root nautilus then unless you emptied root's trash it will still be there I suspect.

---

### Post by 3rdalbum on 2011-11-11
All the lines in mine are commented-out, meaning that nothing in the file actually gets executed by default. Merely creating a blank file with that name will be enough.

---

### Post by troubledone on 2011-11-11
is that what it's called when all the hash marks are in front of each line, like in celestia I guess?

---

### Post by troubledone on 2011-11-11
Actually, that all seemed to do it.  Thanks y'all!

---

