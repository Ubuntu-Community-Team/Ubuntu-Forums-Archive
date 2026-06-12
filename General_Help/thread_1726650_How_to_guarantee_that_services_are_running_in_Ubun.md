---
title: "How to guarantee that services are running in Ubuntu?"
date: 2011-04-11
forum: General Help
---

### Post by aldav on 2011-04-11
Hello, I am working in a project that requires  multiple PC's to run a process. However, the process must be running at all times in all machines. How can I guarantee this? I have heard about Heartbeat, but, frankly, I followed the online tutorial in the project page and could not manage to get it run with 3 PC's and I didn't understand if Heartbeat could solve my problem. Please, any help would be much appreciated.
Thanks

---

### Post by seawolf167 on 2011-04-11
You could make a simple BASH script that searches for it

```
#!/bin/sh
if ps -ef | grep -v grep | grep *-*i* processname*
then echo "*processname *is up"
else "*processname *is down"
fi
```

---

### Post by Cheesehead on 2011-04-11
Use Upstart. It will start your process upon boot, and (optionally) respawn the process if it dies. There are many other controls possible.

Upstart is already part of every Ubuntu install. You can see sample Upstart service config files in /etc/init. More information is at [http://upstart.ubuntu.com]("http://upstart.ubuntu.com")

---

