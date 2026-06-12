---
title: "reload init.d process from within a script"
date: 2010-03-04
forum: General Help
---

### Post by edpatterson on 2010-03-04
I am trying to have squid reload it's config files from with a script run via cron (much appreciation for the prevous help with the date check and touching to diesch!)
```

#!/bin/bash
if [ /etc/squid/lists/staff.sem -ot /etc/squid/lists/staff ]; then
  /etc/init.d/squid reload
  touch -r /etc/squid/lists/staff /etc/squid/lists/staff.sem
fi

```
The above fails with /etc/init.d/squid: No such file or directory. Entering the exact same command at the # prompt works just fine. Enclosing the command in backticks makes the error go away, but the config files are not reloaded. I know the if statement is being processed as the file date and time stamps are sync'd and I have to touch the .sem file each time for testing.

Even stranger is if I make a file justSync.sh
```

#!/bin/bash
/etc/init.d/squid reload

```
then execute it, the config files reload.

I am stymied. I have no idea why the init.d line will not execute from within an if then block.

Ed

---

### Post by undecim on 2010-03-04
If you run the first script manually, does it cause the same error?

What about if you run justSync.sh from a cron job?

---

### Post by undecim on 2010-03-04
After installing squid and looking through /etc/init.d/squid, this command can be used as alternative to /etc/init.d/squid reload:
```
/usr/sbin/squid -k reconfigure
```

That's the command that the init script uses. Only problem is that this action won't be logged, so it's probably best if you get the init script working.

---

### Post by edpatterson on 2010-03-04
> **undecim said:**
> If you run the first script manually, does it cause the same error?

What about if you run justSync.sh from a cron job?

Yes, running it manually touches the files but does not reload the configs.

Running justSync.sh from a cron works. I initially checked messages not syslog.

I would prefer to use the init.d file(s) as I have 2 instances running.

Thanks for the help
Ed

---

### Post by undecim on 2010-03-04
What if you try "sh /etc/init.d/squid reload"?

---

### Post by edpatterson on 2010-03-04
> **undecim said:**
> 
What about if you run justSync.sh from a cron job?

This just keeps getting better and better.

I commented out the '/etc/init/d/squid reload' line and replaced it with /root/bin/justSync.sh and it works.

I would *really* like to know why that is. There is no typo or extraneous characters anywhere in the file

At least it is working, but I do not have warm fuzzies about how it is working.

Ed

---

### Post by undecim on 2010-03-04
> **edpatterson said:**
> This just keeps getting better and better.

I commented out the '/etc/init/d/squid reload' line and replaced it with /root/bin/justSync.sh and it works.

I would *really* like to know why that is. There is no typo or extraneous characters anywhere in the file

At least it is working, but I do not have warm fuzzies about how it is working.

Ed

Very odd. I'm stumped, but glad to see you got it working.

---

