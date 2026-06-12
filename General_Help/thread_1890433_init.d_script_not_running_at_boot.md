---
title: "init.d script not running at boot"
date: 2011-12-03
forum: General Help
---

### Post by smee204 on 2011-12-03
I am trying to automount a encrypted truecrypt partition on my ubuntu encrypted lvm system. 
I have created a init.d script which works perfectly once the system is booted and run manually 
e.g. $/etc/init.d/truecrypt start

However it does not seem to run at boot as when I log the partition is not mounted.
The script is executable and owned by root.
I added it using sudo update-rc.d truecrypt defaults 99 01

Any ideas why this is not working?

My script is shown.
```
#!/bin/bash
#
#   
#
# Mounts the /home partition with truecrypt.
#
# chkconfig: 2345 99 01
# description: Truecrypt

# processname: truecrypt


[ -x /usr/bin/truecrypt ] || exit 1

RETVAL=0
prog="truecrypt" 
desc="Truecrypt" 

start() {
   /usr/bin/truecrypt -t -p password -k "" --protect-hidden=no /dev/sda4 /media/data
   RETVAL=$?
   [ $RETVAL -eq 0 ] 
   echo
}

stop() {
   echo "Unmounting encrypted disks." 
   /usr/bin/truecrypt -d
   RETVAL=$?
   [ $RETVAL -eq 0 ]
   return $RETVAL
}

case "$1" in
  start)
   start
   ;;
  stop)
   stop
   ;;
  restart)
   stop
   start
   RETVAL=$?
   ;;
  condrestart)
        [ -e /var/lock/subsys/$prog ] && restart
   RETVAL=$?
   ;;
  *)
   echo $"Usage: $0 {start|stop|restart|condrestart}" 
   RETVAL=1
esac

exit $RETVAL 
```

---

### Post by Lars Noodén on 2011-12-03
Did you install it to the various runlevel directories using [update-rc.d](http://manpages.ubuntu.com/manpages/precise/en/man8/update-rc.d.8.html)?  It's not enough to have it in [font=Courier New]/etc/init.d/[/font] alone.  It must also be in [font=Courier New]/etc/rc2.d/[/font] - [font=Courier New]/etc/rc6.d/[/font]

---

### Post by smee204 on 2011-12-03
Yes I used  sudo update-rc.d truecrypt defaults 99 01
and I checked it is in /etc/rc2.d

---

### Post by dcstar on 2011-12-03
> **smee204 said:**
> I am trying to automount a encrypted truecrypt partition on my ubuntu encrypted lvm system. 
I have created a init.d script which works perfectly once the system is booted and run manually 
e.g. $/etc/init.d/truecrypt start
..........

Something wrong with /etc/rc.local ?

---

### Post by azmyth on 2011-12-03
I ran into this today as I was starting my No IP script in rc.local and it stopped when I upgraded to 11.10. I could be wrong but my research showed that rc.local isn't being used due to upstart. I tried to set my No IP script in upstart without any luck. I ended up just running the scipt from the autostart directory as I use KDE. You could do the same for gnome.

---

### Post by smee204 on 2011-12-04
I am also using 11.10 so maybe that is the problem. I will have to look into another way to run it. Thanks for the info!

---

### Post by Lars Noodén on 2011-12-04
I have 11.10 and just verified that [font=Courier New]/etc/rc.local[/font] does work.

---

### Post by smee204 on 2011-12-05
Thanks! Ok, mmm back to debugging!

---

### Post by wgregori on 2011-12-22
Any word on this problem.  I'm also running Ubuntu 11.10.  

my script is sitting in etc/inid.d.  I ran 

update-rc.d virtualboxshare defaults 

It completed successfully.

but my script does not run.

### BEGIN INIT INFO
# Provides:          virtualboxshare
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO

mount -t vboxsf -o uid=1000,gid=1000 rets_data /mnt/rets


I can't find where boot script execution is logged.  Can someone tell me how to log these events?
Thanks
Wayne

---

### Post by Lars Noodén on 2011-12-22
> **wgregori said:**
> 
I can't find where boot script execution is logged.  Can someone tell me how to log these events?


You could add a line to your script that calls [logger](http://manpages.ubuntu.com/manpages/oneiric/en/man1/logger.1.html).

---

