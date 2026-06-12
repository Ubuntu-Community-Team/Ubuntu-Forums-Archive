---
title: "Mount command no longer runs at boot from /etc/init.d/rc.local"
date: 2010-07-06
forum: General Help
---

### Post by RockDawg on 2010-07-06
I run XBMC media center software which is built on a minimal Ubuntu install.  I was running a version built on Karmic and I had the following line in my /etc/init.d/rc.local and it always ran without a hitch:

```
mount -t cifs -o file_mode=0777,dir_mode=0777 //192.168.1.20/disk7/xbmc_thumbs/Thumbnails  /home/kevin/.xbmc/userdata/Thumbnails
```

Recently, I upgraded to a version built on Lucid and now that fails to create the mount on boot up.  Am I doing something wrong or did something change?  Here is the entire contents of the file:

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
        if [ -x /etc/rc.local ]; then
                [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
                /etc/rc.local
                ES=$?
                [ "$VERBOSE" != no ] && log_end_msg $ES
                return $ES
        fi
}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

mount -t cifs -o file_mode=0777,dir_mode=0777 //192.168.1.20/disk7/xbmc_thumbs/Thumbnails  /home/kevin/.xbmc/userdata/Thumbnails

```

---

### Post by Ozymandias_117 on 2010-07-06
1. Why put it in rc.local? Why not put it in fstab?

2. I may be wrong, but I think cifs requires a credentials file...

> cifs still uses a credentials file to avoid the need to enter a password. If you do not use a credentials file, you will mount a samba share with sudo and enter your username and password in a terminal.

```
//Server/share /mnt/samba cifs users,auto,credentials=/path/credentials_file,noexec,noperm 0 0
```
Server = Name (if in /etc/hosts) or IP Address of samba server.
share = Name of shared directory (folder).
/mnt/samba = your desired mount point.
/path/credentials_file = full path to your credentials file. A credentials file should be owned by root (permissions 400) and contain two lines :
```
username = samba_user
password = samba_user_password
```
samba_user = samba user (on server).
samba_user_password = samba user password (on server).


---

