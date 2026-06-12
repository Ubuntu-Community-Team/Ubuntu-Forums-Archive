---
title: "Help in making a script to be run with crontab"
date: 2010-06-29
forum: General Help
---

### Post by Paulplex on 2010-06-29
Morning all,

Not strictly being applied to an Ubuntu distro but Linux all the same...

Our company run a database server referenced by a number of mail servers; the database server is very soon to be replaced since it's old, decrepit and not as secure as it should be - indeed, when it decides it's had enough, the MySQL process will simply stop.

You can restart MySQL if you need to quite easily; using Putty, I'll connect to the box and run the command:

[FONT="Courier New"]/etc/rc.d/init.d/mysqld restart[/FONT]

...which restarts MySQL and things are fine again - for a bit.

What I want to do (sorry for the waffle thus far) is use crontab to restart this every thirty minutes, if required; the code I could use for this would be:

[FONT="Courier New"]*/30 * * * * /etc/rc.d/init.d/mysqld restart[/FONT]

...however, what would be better is to have this run a separate script instead, which will only restart mysqld if it's not currently running.

Using [FONT="Courier New"]/etc/rc.d/init.d/mysqld status[/FONT] you can get a response of either *mysqld (pid 8354) is running...* or *mysqld is stopped* - how can I use this information in a script so that mysqld is only restarted if every thirty minutes a check comes back to say it's stopped?

Yes, I'm very much the noob when it comes to scripting and any help would be greatly appreciated; this current server is replaced by someone who knows what he's doing in a few weeks but this will ensure less disruption to those who rely on the current incarnation...

---

### Post by justleen on 2010-06-29
I would use probably something like this:
```

#!/bin/bash
STATE=$(/etc/init.d/mysql status)
if [[ $STATE == '*stopped*' ]]; then
  echo 'Looks mysql is stopped... restarting..'
  /etc/init.d/mysql start
else
  echo 'all  is well, mysql is still running'
fi

```

---

### Post by Paulplex on 2010-06-29
> **justleen said:**
> I would use probably something like this:
```

#!/bin/bash
STATE=$(/etc/init.d/mysql status)
if [[ $STATE == '*stopped*' ]]; then
  echo 'Looks mysql is stopped... restarting..'
  /etc/init.d/mysql start
else
  echo 'all  is well, mysql is still running'
fi

```
Thank you very much; I owe you a beer! ):P

---

