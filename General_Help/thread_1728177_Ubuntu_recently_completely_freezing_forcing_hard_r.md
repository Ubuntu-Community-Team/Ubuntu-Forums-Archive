---
title: "Ubuntu recently completely freezing forcing hard restart"
date: 2011-04-13
forum: General Help
---

### Post by excetara2 on 2011-04-13
Ubuntu has been freezing completely recently. I am not sure of the issue. The main things i have changed recently is dropbox as far as I know. Not to long ago I updated VirtualBox. I am not sure if it always happens when I'm running a Virtual machine.

What log should I check for system crashes? I know the time it occurred just wasn't sure what log to check or where to start investigating.

---

### Post by excetara2 on 2011-04-13
Does anyone know where the VBox log file is? This is all that is in the syslog before restart:

Apr 14 01:01:32 bigtyme-desktop kernel: [31471.816871] lo: Disabled Privacy Extensions
Apr 14 01:09:02 bigtyme-desktop CRON[8161]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr 14 01:17:01 bigtyme-desktop CRON[8301]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 14 01:39:02 bigtyme-desktop CRON[9119]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr 14 02:09:01 bigtyme-desktop CRON[9625]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

---

