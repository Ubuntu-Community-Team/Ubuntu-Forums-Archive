---
title: "Problems integrating xinetd, git-deamon, and windows version of  git"
date: 2011-06-15
forum: General Help
---

### Post by afischer.aea on 2011-06-15
I am trying to get a git repo up and running for a project.  I currently am running git-daemon through xinetd, and can pull from the repo but not push back to it. 

/etc/xinetd.d/git-daemon currently looks like this:

```

service git
{
socket_type = stream
wait = no
user = gitman
group = gitman
server = /usr/bin/git-daemon
server_args = --inetd --reuseaddr --base-path=/home/gitman/root --export-all 
--enable=receive-pack --verbose --syslog /home/gitman/root
log_on_failure += USERID
}

```and /var/log/messages looks like this:
```

Jun 15 15:25:14 dev1 xinetd[27922]: xinetd Version 2.3.14 started with libwrap
 loadavg labeled-networking options compiled in.
Jun 15 15:25:14 dev1 xinetd[27922]: Started working: 1 available service
Jun 15 15:25:43 dev1 xinetd[27922]: START: git pid=27927 from=209.XXX.XXX.106
Jun 15 15:25:43 dev1 git-daemon[27927]: Extended attributes (22 bytes) exist 
<host=dev1.aea.us.com>
Jun 15 15:25:43 dev1 git-daemon[27927]: Request receive-pack for '/EPA.git'

```for some reason, the push request goes through, then stops and hangs.  I went to lunch for an hour, and still nothing.  Any thoughts?

---

### Post by afischer.aea on 2011-06-16
Anyone there? 24 hours, and no love?

---

### Post by afischer.aea on 2011-06-16
As a development, when I try to push something, two processes are spawned, git and git-daemon.  they then both promptly sleep.  I tried to send each seperately a SIGALRM, but when one recieves, both exit and die.

---

