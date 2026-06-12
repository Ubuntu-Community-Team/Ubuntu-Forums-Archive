---
title: "SFTP / SSHFS  Problems"
date: 2012-08-03
forum: General Help
---

### Post by nmaster on 2012-08-03
I noticed that when I connect to a particular server with sftp or sshfs, the connection would not stay open.  This would happen at the command line or if I used pcmanfm.  I wasn't getting an error message so I tried Filezilla. This is what happened:
```

Command:    Pass: **********
Status:    Connected to $HOST
Status:    Retrieving directory listing...
Command:    pwd
Response:    Current directory is: "$DIR"
Command:    ls
Status:    Listing directory $DIR
Status:    Calculating timezone offset of server...
Command:    mtime ".backup"
Response:    1343184232
Status:    Timezone offsets: Server: -25200 seconds. Local: -14400 seconds. Difference: 10800 seconds.
Status:    Directory listing successful
Error:    Connection closed by server with exitcode 129

```( I removed the actual hostname and directory)

There is indeed a 3 hour (10800 second) time difference between my location and the server.

When I simply ssh into the server this does not happen.

I thought that it might be a timeout so I added "ServerAliveInterval 5" to ~/.ssh/config.  This did not change the behavior.

I do not have root access to the server (it is a university server), but it is running Ubuntu 12.04 LTS x86_64.

Does anyone know what "exitcode 129" means? I was unable to find any hints through a search engine.

---

### Post by papibe on 2012-08-03
Hi nmaster.

Do you have access to the server logs?

This would give us some clues:
```
grep sshd /var/log/auth.log
```
Regards.

---

### Post by nmaster on 2012-08-03
> **papibe said:**
> Hi nmaster.

Do you have access to the server logs?

This would give us some clues:
```
grep sshd /var/log/auth.log
```Regards.

sorry, i don't have access to the log:
```

$ grep sshd /var/log/auth.log 
grep: /var/log/auth.log: Permission denied
$ ls -l /var/log/auth.log 
-rw-r----- 1 root root 28594 Jul 12 00:45 /var/log/auth.log

```

is there some other way of finding out what "exitcode 129" means?  I could ask the university IT people, but im not sure what they'll tell me when i say i'm not using windows or mac os.

---

### Post by papibe on 2012-08-03
Do you use a key to connect using ssh, or just user and password?

Regards.

---

### Post by nmaster on 2012-08-04
> **papibe said:**
> Do you use a key to connect using ssh, or just user and password?

Regards.
i recall trying to set up keys so that i could do passwordless ssh, but for some reason it didn't work... i removed the keys from the server:
```

nmaster@$HOST:$HOME/.ssh 
$ ls -a
.  ..

```

i currently just use a traditional username/password login.

---

### Post by nmaster on 2012-08-11
bump

---

