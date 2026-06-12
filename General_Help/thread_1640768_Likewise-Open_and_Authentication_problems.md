---
title: "Likewise-Open and Authentication problems"
date: 2010-12-08
forum: General Help
---

### Post by fooraide on 2010-12-08
Hi,

A quick overview of what I am trying to achieve:
[LIST]
A server that authenticates against Active Directory by being joined to a domain through likewise-open
The server is joined successfully to the domain, computer is found in active directory
Running Ubuntu: Linux 2.6.32-26-generic-pae #48-Ubuntu SMP Wed Nov 24 10:31:20 UTC 2010 i686 GNU/Linux / Ubuntu 10.04.1 LTS
Commands like "domainjoin-cli query", "lw-get-status" or "lw-enum-users" work properly
[/LIST]

Now, my problem:
- SSH connections as DOMAIN\\user in SSH result in a permission denied:
```
(/var/log/auth.log)
Dec  8 08:37:34 ubuntu sshd[2204]: Invalid user domain\\user from 192.168.21.139
Dec  8 08:37:34 ubuntu sshd[2204]: Failed none for invalid user domain\\user from 192.168.21.139 port 57603 ssh2
Dec  8 08:37:37 ubuntu sshd[2204]: pam_unix(sshd:auth): check pass; user unknown
Dec  8 08:37:37 ubuntu sshd[2204]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.21.139 
Dec  8 08:37:38 ubuntu sshd[2204]: [module:pam_lsass]pam_sm_authenticate error [login:domain\user][error code:40022]
Dec  8 08:37:39 ubuntu sshd[2204]: Failed password for invalid user domain\\user from 192.168.21.139 port 57603 ssh2

```

- Connections as the same user on server locally shows an entirely different error, the connection will succeed (The MOTD is printed) but then, an error is displayed "User not known to the underlying authentication module", then I am sent back to the login prompt.
```
**(/var/log/auth.log)**
Dec  8 08:31:29 ubuntu login[2136]: pam_unix(login:auth): check pass; user unknown
Dec  8 08:31:29 ubuntu login[2136]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost= 
Dec  8 08:31:30 ubuntu login[2136]: pam_unix(login:account): could not identify user (from getpwnam(DOMAIN\user))
Dec  8 08:31:30 ubuntu login[2136]: pam_env(login:session): No such user!?
Dec  8 08:31:30 ubuntu login[2136]: pam_env(login:session): No such user!?
Dec  8 08:31:30 ubuntu login[2136]: pam_unix(login:session): session opened for user DOMAIN\user by LOGIN(uid=0)
Dec  8 08:31:30 ubuntu login[2136]: User not known to the underlying authentication module

```

It's really weird because likewise-open will even create the home directory for the user as if the connection would have been completed successfully.

Any idaes ? I am at a loss here, I've tried pretty much everything, going as far as reinstalling the server on a clean base. I'm rather used to using likewise-open but this is the first time something like this happens.

Let me know if you'd like any more info to diagnose the issue.

Thanks,

---

### Post by HermanAB on 2010-12-08
Howdy,

The failure is the same in both cases: unknown user.  Everything after that point is just noise.

---

### Post by fooraide on 2010-12-08
After even more exhaustive searches, I've stumbled across this bug:
[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/543733](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/543733)

I've followed the instructions shown here:
[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/543963/comments/8](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/543963/comments/8)

And everything works flawlessly now.

Hope this helps if anyone else has that problem.

Yay !

---

