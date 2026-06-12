---
title: "locate, mlocate, updatedb, find, and cron"
date: 2009-08-01
forum: General Help
---

### Post by SEMW on 2009-08-01
Hi,

I'm trying to make updatedb run weekly rather than daily, since I was finding the long period of disk activity when I turn my computer on annoying, and was rather confused by the various scripts in /etc/cron.daily.

For a start, there is the difference between /etc/cron.daily/mlocate and /etc/cron.daily/find:

mlocate script:
```
#! /bin/bash

set -e

[ -x /usr/bin/updatedb.mlocate ] || exit 0

if which on_ac_power >/dev/null 2>&1; then
    AC_POWER=0
    on_ac_power >/dev/null 2>&1 || AC_POWER=$?
    if [ "$AC_POWER" -eq 1 ]; then
	echo >&2 "On battery power, not running today."
	exit 1
    fi
fi

##

LOCKFILE="/var/lib/mlocate/daily.lock"

trap "rm -f $LOCKFILE" EXIT

if [ -e "$LOCKFILE" ]; then
    echo >&2 "Warning: $LOCKFILE present, not running today."
    exit 1
else
    touch "$LOCKFILE"
fi

##

# See ionice(1)
if [ -x /usr/bin/ionice ] &&
    /usr/bin/ionice -c3 true 2>/dev/null; then
    IONICE="/usr/bin/ionice -c3"
fi

$IONICE /usr/bin/updatedb.mlocate

```

find script:
```
#! /bin/sh
#
# cron script to update the `locatedb' database.
#
# Written by Ian A. Murdock <imurdock@debian.org> and 
#            Kevin Dalley <kevin@aimnet.com>

LOCALUSER="nobody"
export LOCALUSER
if [ -f /etc/updatedb.conf ]; then
  . /etc/updatedb.conf
fi

if getent passwd $LOCALUSER > /dev/null ; then
  cd / && nice -n ${NICE:-10} ionice -c ${IONICE_CLASS:-2} -p ${IONICE_PRIORITY:-7} updatedb 2>/dev/null
else
  echo "User $LOCALUSER does not exist."
  exit 1
fi
```

One of these runs updatedb.mlocate, and the other updatedb; but since updatedb is symlinked to updatedb.mlocate (via /etc/alternatives), this is irrelevent: they are both updating the same database.  The former checks for AC power and a lockfile, the latter doesn't bother.

To add to the complications, there's a varient on the "find" script, also in /etc/cron.daily/, called "find.notslocate.dpkg-new", which is identical except that "-p" in line 15 is replaced by "-n".

So I have three scripts, all of which seem to do pretty much the same thing, all of which are presumably run every day sequentially when I turn the computer on.  No wonder it was taking a while.  (At least I hope they run sequentially; if they're running concurrently then the fact that only one has lock file checks might cause problems...).

So can someone with a fresh Jaunty install look in their /etc/cron.daily/ and tell me which of the three scripts is the one that is supposed to be there now (and so which I can delete as cruft)?  Also, is there any particular reason that the Ubuntu upgrade process doesn't remove old versions of the updatedb script when it adds new ones?

---

### Post by minigeek on 2009-08-01
Hi

/etc/cron.daily/mlocate.

Fresh install off Ubuntu 9.04

:)

---

### Post by SEMW on 2009-08-02
Thanks!

I've made the two 'find' scripts non-executable and moved the 'mlocate' one to cron.weekly.  See how that goes.  Not sure when/why the name was changed when they added the extra content to the scripts, or why the old format wasn't removed when the new one came in, but doesn't really matter; water under the bridge.

---

### Post by unutbu on 2009-08-02
Thank you SEMW, your sig makes me laugh!

---

### Post by MountainX on 2009-08-18
related info:
[http://www.eddieoneverything.com/linux/linux-question-when-does-updatedbmlocat-crondaily-run.php](http://www.eddieoneverything.com/linux/linux-question-when-does-updatedbmlocat-crondaily-run.php)

---

### Post by MountainX on 2009-08-18
> **SEMW said:**
>  Not sure when/why the name was changed when they added the extra content to the scripts, or why the old format wasn't removed when the new one came in...

FWIW:
[http://www.shallowsky.com/blog/linux/install/too-much-updatedb.html](http://www.shallowsky.com/blog/linux/install/too-much-updatedb.html)

---

### Post by mhagger on 2009-09-09
cron scripts are run by /etc/crontab using run-parts, which automatically ignores any files that have "." in their filenames (among other rules; see the run-parts man page.   So "find.notslocate" and "find.notslocate.dpkg-new" will not actually be run.

The "locate" package does not seem critical.  The only thing that required it on my system was "dlocate", which I can definitely do without.  I just purged both of them and that got rid of "/etc/cron.daily/locate", and hopefully a lot of disk IO on wake-from-suspend every morning.

---

### Post by P4man on 2009-09-09
I think its a "bug" that happens when you do a distribution upgrade. It keeps the old updatedb scripts and adds the new one, where it should have disabled the old ones. As a result ppl upgrading hardy > intrepid > jaunty may have 2 or 3 updatedb scripts running.. simultaneously. No wonder they complain its sluggish in the morning ;)

---

### Post by dcstar on 2009-09-09
> **P4man said:**
> I think its a "bug" that happens when you do a distribution upgrade. It keeps the old updatedb scripts and adds the new one, where it should have disabled the old ones. As a result ppl upgrading hardy > intrepid > jaunty may have 2 or 3 updatedb scripts running.. simultaneously. No wonder they complain its sluggish in the morning ;)

Yet another good reason to have a separate /home partition and do fresh installs of new versions rather than upgrades.

I sometimes wonder how better Ubuntu's reputation would be if it defaulted to a separate /home partition, allowing users to reinstall without any loss of user data.

---

