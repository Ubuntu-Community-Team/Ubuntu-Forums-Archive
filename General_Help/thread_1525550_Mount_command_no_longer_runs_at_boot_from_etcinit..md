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

### Post by nemilar on 2010-07-06
It looks like the script is exiting before it reaches your command.

Is there any reason why you didn't put this directly into /etc/fstab?  I think that might be what you really want to do here. 

Putting commands into /etc/rc.local can be tempting because it's so easy, but it's very often the wrong way to do it (I was very guilty of this when I first started with Linux).

---

### Post by RockDawg on 2010-07-07
I really don't know much about Ubuntu/Linux so I'm not really familiar with any of theis.  I looked up fstab on wikipedia and it seems to require a certain format.  What would be the proper way to put that line in fstab?

---

### Post by nemilar on 2010-07-07
I can't test it right now, but I think:

```
//192.168.1.20/disk7/xmbc_thumbs/Thumbnails     /home/kevin/.xbmc/userdata/Thumbnails   cifs    file_mode=0777,dir_mode=0777 0 0

```

Put this on a new line at the end of your /etc/fstab file.  Then try:

```
mount /home/kevin/.xbmc/userdata/Thumbnails
``` 

to see if it is working correctly.

---

### Post by RockDawg on 2010-07-07
Thanks.  I'll try that when I get home tonight.

---

### Post by RockDawg on 2010-07-08
I finally had a chance to try this and it still doesn't work.  Here is my fstab after adding that line:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e1ae2457-de1e-4632-8b83-3916050246a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63a0540e-bee2-4d5d-b27e-cb276742bdff none            swap    sw              0       0
//192.168.1.20/disk7/xmbc_thumbs/Thumbnails     /home/kevin/.xbmc/userdata/Thumbnails   cifs    file_mode=0777,dir_mode=0777 0 0
```

---

### Post by RockDawg on 2010-07-09
I even tried inserting the command further up in rc.local in case nemilar was right and the script ended before getting to that line and it still doesn't work.

I don't get it.

---

### Post by nemilar on 2010-07-09
Can you be more specific about what isn't working?

What's the error you get?

---

### Post by RockDawg on 2010-07-09
I don't see any error per se (not sure which log would show it), but /home/kevin/.xbmc/userdata/Thumbnails doesn't show the same contents as //192.168.1.20/disk7/xmbc_thumbs/Thumbnails.

---

### Post by nemilar on 2010-07-09
Can you post the output of:

```
mount
```

Also, run the mount command that you're using above, manually from the command line.  Does it present an error?  What is the output of "mount" after you run that command?

---

### Post by RockDawg on 2010-07-09
Here is the result of 'mount':

```
kevin@ubuntu:~$ mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=894768k,nr_inodes=216054,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=                            000)
/dev/disk/by-uuid/e1ae2457-de1e-4632-8b83-3916050246a9 on / type ext4 (rw,relati                            me,errors=remount-ro,barrier=1,data=ordered)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
none on /lib/init/rw type tmpfs (rw,nosuid,relatime,mode=755)

```

When I run 'sudo mount -t cifs -o file_mode=0777,dir_mode=0777 //192.168.1.20/disk7/xbmc_thumbs/Thumbnails  /home/kevin/.xbmc/userdata/Thumbnails', I don't get any error and the mount is created fine.  Here is the result of 'mount' after I run that command and the mount is indeed created:

```
kevin@ubuntu:~$ mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=894768k,nr_inodes=216054,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/disk/by-uuid/e1ae2457-de1e-4632-8b83-3916050246a9 on / type ext4 (rw,relatime,errors=remount-ro,barrier=1,data=ordered)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
none on /lib/init/rw type tmpfs (rw,nosuid,relatime,mode=755)
//192.168.1.20/disk7/xbmc_thumbs/Thumbnails on /home/kevin/.xbmc/userdata/Thumbnails type cifs (rw,mand,relatime,unc=\\192.168.1.20\disk7,username=root,uid=0,noforceuid,gid=0,noforcegid,addr=192.168.1.20,file_mode=0777,dir_mode=0777,prepath=\xbmc_thumbs\Thumbnails,serverino,rsize=16384,wsize=57344)
```

---

### Post by RockDawg on 2010-07-10
Anybody have any ideas what could be wrong?

---

