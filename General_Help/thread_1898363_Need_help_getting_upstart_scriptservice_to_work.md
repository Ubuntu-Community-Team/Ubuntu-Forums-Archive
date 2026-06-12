---
title: "Need help getting upstart script/service to work"
date: 2011-12-21
forum: General Help
---

### Post by paulrichards on 2011-12-21
Hello,

For some reason this script/serivce does not appear to run on startup. I created the script myself, along with the program it runs. The program runs fine when run as root manually. The program is in /usr/sbin.
I installed the following script (resetmsmice.conf) into /etc/init:

```

# resetmsmice
# 
# repairs abnormally fast vertical scroll wheel issues with
# certain Microsoft wireless mice and X.org.
# run 'fixmsmice --help' for more info.

description "Resetting any Wireless Microsoft mice that are known to cause scroll wheel issues with X.org"
author "paulrichards321@gmail.com"

start on (startup
    and started filesystem
    and started desktop-session-start)

task

exec resetmsmice 
```

The program resetmsmice, logs to syslog. When run as root it runs fine, however, it does not seem to be run at all on startup.

---

### Post by paulrichards on 2011-12-23
Got it to work by removing the 'task' line.

Apparently that makes it behave different on the dependacies. More info here if anyone is interested: [http://upstart.ubuntu.com/cookbook/#id182](http://upstart.ubuntu.com/cookbook/#id182)

---

