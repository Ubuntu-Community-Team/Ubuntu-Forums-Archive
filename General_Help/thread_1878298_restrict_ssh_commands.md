---
title: "restrict ssh commands"
date: 2011-11-09
forum: General Help
---

### Post by Bradburts on 2011-11-09
I want to filter ssh commands. I have an authorized_keys file of: 
```
 no-port-forwarding,no-X11-forwarding,no-agent-forwarding,no-pty, command="/home/rsnapshot/.ssh/restrict-ssh.sh" ssh-rsa my public key== rsnapshot@Home

```
 
restrict-ssh.sh contains:
 
```

#!/bin/sh
echo "Rejected"

```
 
Every command I have tried works though!
Its unusual for things to work for me, the moment I want to stop them working they work!
What am I doing wrong? Is there a log file I can check?

---

