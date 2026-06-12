---
title: "Expect script cronjob running but dying prematurely"
date: 2011-10-15
forum: General Help
---

### Post by Cuddles McKitten on 2011-10-15
I've got an expect script to run aptitude and update my packages.  It works quite nicely when run directly from the command line.  However, when the cronjob I set up runs it (as root), it dies very quickly.  I 'tee' the output into a log, and in the "aptitude update" stage, it only updates maybe 1/6 of the total sources before inexplicably terminating.

Does anyone have any idea what I might be doing wrong or have any way I might be able to diagnose why the script is quitting early?

Here's the script:
```

#!/usr/bin/expect -f

set timeout 180
spawn aptitude update

expect {
   eof
}

set timeout 3600
spawn aptitude safe-upgrade

expect {
    "Y/n" { send "y\r"; expect { eof } } \
    eof
}

```And here's my crontab line:
```
        *       */12    *       *       *       /home/jimmy/script/patch.sh | tee /home/jimmy/script/patch.log

```

---

