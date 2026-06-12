---
title: "create upstart job - fail"
date: 2012-06-10
forum: General Help
---

### Post by stephan0h on 2012-06-10
Hi, 
On Ubuntu 12.04 ... I want to create an upstart job for

```
syncevo-http-server http://lalhost:9000/syncevolution
```

This is my job

```

# myservice - myservice job file

description "syncevolution http server"
author "stephan"

# Stanzas
#
# Stanzas control when and how a process is started and stopped
# See a list of stanzas here: http://upstart.ubuntu.com/wiki/Stanzas#respawn

# When to start the service
start on started network
stop on stopping network
stop on starting shutdown

console output

# Automatically restart process if crashed
#respawn

# Start the process
exec  syncevo-http-server http://lalhost:9000/syncevolution

```

But it does not seem to get started. When I start it manually, it returns a pid, but the process is not existing when I do a ps, and when I stop the job it returns "unkown instance".

```

stephan@rechenmonster:/etc/init$ sudo start syncevo-http-server
syncevo-http-server start/running, process 10679
stephan@rechenmonster:/etc/init$ ps -ef|grep 10679
stephan  10681  4088  0 15:06 pts/4    00:00:00 grep 10679
stephan@rechenmonster:/etc/init$ sudo stop syncevo-http-server
stop: Unknown instance: 

```

 Any ideas?

Thanks,
Stephan

---

