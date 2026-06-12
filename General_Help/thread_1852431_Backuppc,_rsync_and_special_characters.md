---
title: "Backuppc, rsync and special characters"
date: 2011-09-30
forum: General Help
---

### Post by Kimm3 on 2011-09-30
Hey,
I've installed backuppc on an Ubuntu 11.04 server, basically followed this guide:
[http://www.cs.umd.edu/~cdunne/projs/backuppc_guide.html](http://www.cs.umd.edu/~cdunne/projs/backuppc_guide.html)
 
The idea is to backup windows machines with backuppc over ssh/rsync (installed with cygwin), and it works great until it comes to a share name that includes any special characters like å,ä or ö. Backuppc gives me the error:
 
14:53:13 Aborting backup up after signal PIPE
14:53:14 Got fatal error during xfer (aborted by signal=PIPE)
 
This happens both to Windows 7 and XP machines.
 
When I try to do a manual ssh/rsync with the command:
```
rsync -avz -e ssh *remoteuser@remoteip*:/cygdrive/c/testå
```
I get the error "*rsync: link_stat "/cygdrive/c/test\#345" failed: No such file or directory (2)"... *If I ssh to the machine I can see the folder but the å is not displayed correctly (wierd chars instead).
 
I've googled alot and found that could be something with the cygwin install of rsync...? Or maybe just something with rsync in general? Either way, i'm new to all this and appreciate all the help I can get...

---

