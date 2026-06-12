---
title: "update-rc.d ignoring my init script's runlevels"
date: 2011-02-01
forum: General Help
---

### Post by supremedalek on 2011-02-01
Let's say I have a init script, etc/init.d/strangeScript, that starts like this:

```
#! /bin/sh

### BEGIN INIT INFO
# Provides:          strangeScript
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start and stop something strange
# Description:       You really don't want to know partition 
is up
### END INIT INFO

PATH=/bin:/usr/bin:/sbin:/usr/sbin
MOUNT=/bin/mount
UMOUNT=/bin/umount
INIT_PATH=/etc/init.d

. /lib/lsb/init-functions

case "$1" in
start)
```

So I want to let update-rc.d create all the little start/stop links for the different runlevels. But, something does not seem right here: 

```
root@system:~# update-rc.d strangeScript enable
update-rc.d: warning: strangeScript start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: strangeScript stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
 System start/stop links for /etc/init.d/strangeScript do not exist.
root@system:~# 
```

Why is it not only complaining my runlevels do not match the defaults, which they do, but also is refusing to create the links to the proper runlevels? This is 10.04LTS if that matters.

---

### Post by sisco311 on 2011-02-01
Invoked with the disable or enable option, update-rc.d tries to modify the existing runlevel links. If they don't exist, it throws an error.

So, you have to create the links. In most cases you can use the default option:
```
update-rc.d -f scriptname defaults
```

For more details and examples check out the man page:
```
man update-rc.d
```

---

### Post by oldmilwaukee on 2012-05-22
from the man:
runlevel information in the init.d script LSB com-        ment header is used (..)  Such header is required to be present  in        init.d  scripts.   See the [insserv(8)]("http://www.unix.com/man-page/All/8/insserv/") manual page for details about the        LSB header format. 

Example:

### BEGIN INIT INFO
# Provides:          apache2
# Required-Start:    $local_fs $remote_fs $network $syslog
# Required-Stop:     $local_fs $remote_fs $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# X-Interactive:     true
# Short-Description: Start/stop apache2 web server
### END INIT INFO

---

