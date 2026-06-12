---
title: "account login problem"
date: 2012-05-27
forum: General Help
---

### Post by faldo on 2012-05-27
hi i have problem with my login account... this is my log:

> May 27 23:54:51 user gdm-session-worker[1354]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "user"
May 27 23:54:58 user gdm-session-worker[1354]: pam_unix(gdm:session): session opened for user user by (uid=0)
May 27 23:54:58 user gdm-session-worker[1354]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 27 23:54:58 user gdm-session-worker[1354]: pam_unix(gdm:session): session closed for user user
May 27 23:55:05 user gdm-session-worker[1612]: pam_succeed_if(gdm:auth): requirement "user ingroup 

and syslog say PERMISSION DENIED:

> May 28 03:19:13 user gdm-session-worker[1460]: WARNING: unable to log session
May 28 03:19:13 user gdm-session-worker[1460]: WARNING: could not save session and language settings: Failed to create file '/home/user/.dmrc.X4E8EW': [COLOR="Red"]**Permission denied**[/COLOR]
May 28 03:19:13 user acpid: client 1247[0:0] has disconnected
May 28 03:19:13 user acpid: client connected from 1572[0:0]
May 28 03:19:13 user acpid: 1 client rule loaded

Now i'm logged as root and as you can see i've mount the user directory without problem trough the "ecryptfs-mount-private":
> user@user:/root$ ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [***************] into the user session keyring
user@user:/root$ 

but... anything appens :-(
help me!!!

---

### Post by faldo on 2012-05-29
anybody knows to solve my problem?!

---

