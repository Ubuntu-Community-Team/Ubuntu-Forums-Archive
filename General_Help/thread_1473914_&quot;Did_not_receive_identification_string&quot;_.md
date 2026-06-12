---
title: "&quot;Did not receive identification string&quot; in auth.log"
date: 2010-05-05
forum: General Help
---

### Post by Altay_H on 2010-05-05
```
May  4 20:32:30 server sshd[19955]: Did not receive identification string from 192.168.1.5
May  4 20:42:18 server sshd[20012]: Did not receive identification string from 192.168.1.5
May  4 20:52:19 server sshd[20050]: Did not receive identification string from 192.168.1.5
May  4 21:02:15 server sshd[20142]: Did not receive identification string from 192.168.1.5
May  4 21:12:16 server sshd[20190]: Did not receive identification string from 192.168.1.5
May  4 21:22:15 server sshd[20228]: Did not receive identification string from 192.168.1.5
May  4 21:32:22 server sshd[20268]: Did not receive identification string from 192.168.1.5
May  4 21:42:16 server sshd[20300]: Did not receive identification string from 192.168.1.5
May  4 21:52:17 server sshd[20434]: Did not receive identification string from 192.168.1.5
May  4 22:02:36 server sshd[20484]: Did not receive identification string from 192.168.1.5
May  4 22:12:45 server sshd[20523]: Did not receive identification string from 192.168.1.5
May  4 22:22:29 server sshd[20564]: Did not receive identification string from 192.168.1.5
```

I noticed the above showing up in my /var/log/auth.log and was wondering if someone could explain what they mean. It's from a local IP I use Putty to SSH in from, so I'm sure it's not some sort of hack attempt, but I'm really not sure what it might be. Thanks for any help.

---

### Post by scmizer on 2010-10-30
1) Are you using public/private keys to secure your SSH connection? 
2) Have you tried running PuTTY in verbose mode? That might give you more info about how PuTTY is attempting to authenticate.
3) The regularity of the timestamp series looks like a running service rather than a manual login attempt. Are you running anything else that might be attempting to access your server? Do the timestamps correlate to your logins via PuTTY, or do they appear even when you shut down that process?

---

### Post by realloc on 2011-01-09
I am seeing almost the same thing.  Every 30 secs I get a failed connection attempt... but for me it comes from ::1 (the IPv6 localhost address). I upgrades my sshd logging level to "DEBUG" and this is what I get:

```

Jan  8 21:13:24 pbx2 sshd[24826]: Did not receive identification string from ::1
Jan  8 21:13:55 pbx2 sshd[24776]: debug1: Forked child 24864.
Jan  8 21:13:55 pbx2 sshd[24864]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jan  8 21:13:55 pbx2 sshd[24864]: debug1: inetd sockets after dupping: 3, 3
Jan  8 21:13:55 pbx2 sshd[24864]: Connection from ::1 port 46125
Jan  8 21:13:55 pbx2 sshd[24864]: Did not receive identification string from ::1
Jan  8 21:14:25 pbx2 sshd[24776]: debug1: Forked child 24902.
Jan  8 21:14:25 pbx2 sshd[24902]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jan  8 21:14:25 pbx2 sshd[24902]: debug1: inetd sockets after dupping: 3, 3
Jan  8 21:14:25 pbx2 sshd[24902]: Connection from ::1 port 46143
Jan  8 21:14:25 pbx2 sshd[24902]: Did not receive identification string from ::1
Jan  8 21:14:55 pbx2 sshd[24776]: debug1: Forked child 24940.
Jan  8 21:14:55 pbx2 sshd[24940]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jan  8 21:14:55 pbx2 sshd[24940]: debug1: inetd sockets after dupping: 3, 3
Jan  8 21:14:55 pbx2 sshd[24940]: Connection from ::1 port 46161
Jan  8 21:14:55 pbx2 sshd[24940]: Did not receive identification string from ::1
Jan  8 21:15:26 pbx2 sshd[24776]: debug1: Forked child 24979.
Jan  8 21:15:26 pbx2 sshd[24979]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jan  8 21:15:26 pbx2 sshd[24979]: debug1: inetd sockets after dupping: 3, 3
Jan  8 21:15:26 pbx2 sshd[24979]: Connection from ::1 port 46179
Jan  8 21:15:26 pbx2 sshd[24979]: Did not receive identification string from ::1
```

I haven't seen this before.  I do have OpenVPN running... but I don't think that matters.  (And OpenVPN has nothing to do with sshd, so I'm stumped.)

I have bridged config set up with a br0 also... and I'm running Asterisk and FreePBX.  (Just tossing out possible troublemakers here...)

It can't be cron because cron only runs every minute (at the soonest).  Hmm... maybe a looping gdm that won't boot?  Dunno...

This is on a 10.4 Virtual Machine running under KVM.


[EDIT]
Found it.  This is a known issue with FreePBX.  It polls port 22 for listening (as part of the FreePBX monitoring), resulting in the errors.

[http://www.freepbx.org/v2/ticket/3461](http://www.freepbx.org/v2/ticket/3461)

The FreePBX bug is not fixed and has been given low priority... *sigh*

---

