---
title: "banning ssh &quot;possible break in attempt&quot;"
date: 2012-09-14
forum: General Help
---

### Post by hwttdz on 2012-09-14
I was looking at my auth.log and saw quite a few messages along the lines of:

```
Sep 14 10:55:59 poseidon sshd[29450]: Address 64.34.162.96 maps to [redacted, never visit addresses from messages like these], but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Sep 14 10:55:59 poseidon sshd[29450]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=64.34.162.96  user=root
Sep 14 10:56:01 poseidon sshd[29450]: Failed password for root from 64.34.162.96 port 44716 ssh2
Sep 14 10:56:01 poseidon sshd[29450]: Received disconnect from 64.34.162.96: 11: Bye Bye [preauth]
```

Is there a way I can block this sort of login?  Could that result in blocking myself when I try to ssh to my machine remotely if the machine I'm coming from doesn't have dns set up properly?

I'm setting up fail2ban as well and asked a question about that in a different thread.  That said overall I'm not too worried about this.  I can't see a reason why my machine should be subject to a concerted effort, and short of an amazon cluster they're going to have a tough time with the password.

---

