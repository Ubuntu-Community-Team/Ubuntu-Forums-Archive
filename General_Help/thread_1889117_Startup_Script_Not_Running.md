---
title: "Startup Script Not Running"
date: 2011-11-30
forum: General Help
---

### Post by GlxyDs on 2011-11-30
Hi,

I'm trying to install a startup script to set the volume of my machine at system boot. The following steps are what I have done to make it work (from my understanding). I've done this with a similar service and it works, so I'm confused as to why my new script isn't functioning properly. I can manually start it but it doesn't start at the system boot. 

1. I wrote the following script:
> #!/bin/sh

### BEGIN INIT INFO
# Provides:          Volume Control
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Description:       Sets the volume to 100%
### END INIT INFO

# Author: MisterShred

case "$1" in
start)
         sudo -u support amixer set PCM 100 1>/dev/null 2>&1 &
         echo "Volume has been set to 100%."
         exit 1
       ;;

stop)
       sudo -u support amixer set PCM 0% 1>/dev/null 2>&1
       echo "Volume has been set to 0%."
       ;;

restart)
       $0 stop
       $0 start
       ;;

reload|force-reload)
       $0 stop
       $0 start
       ;;
*)      log_action_msg "Usage: /etc/init.d/volumecontrol {start|stop|restart|re$
       exit 2
       ;;
esac
exit 02. I made the script executable.
> chmod +x /etc/init.d/volumecontrol3. I added the volumecontrol script to update-rc.d using the defaults.
> sudo update-rc.d volumecontrol defaultsSo from my understanding (and previous experience) that should work. Any ideas?

---

### Post by gennatolls on 2011-11-30
Hi,

Sorry I know this is Ubuntu but in Arch you have to add the different executable files in your daemon list at /etc/rc.conf for the daemons to be started upon boot. I'm uncertain where that equivalent file is on Ubuntu but may be a direction to look for your solution. I'm guessing you want this to take effect system wide and not per user so just adding it to the "Startup Applications" once logged in wouldn't solve your problem? Also to note, the different daemons start up in a particular order (I can't tell you because I'm unsure of the where to find the bloody conf file). Maybe your script is trying to start before alsa starts. I had this problem when trying to run Conky upon startup with a script, I had to make it sleep for 10 seconds to give xorg enough time to startup. Hope this helps. Good Luck

---

### Post by Azdour on 2011-12-01
Hi,

I would first put some echo statements in the start part of the script that output to a log. Then you can see if its being called.

If it is being called but the volume is not changing it, and this is only a guess, then maybe the volume cannot be changed on boot-up.
You could then look at a different way to do this, e.g. in Ubuntu (10.04) System | Preferences | Startup - then you could have a script to set the volume when you login.

If it is not being called I would check the following directories:
```

/etc/rc2.d
/etc/rc3.d
/etc/rc4.d
/etc/rc5.d

```

When you ran update-rc.d it should have put links in the above directories to your script in /etc/init.d

Just to clarify, you said that when you run it manually it works? e.g.:
```
sudo service <script_name>
```

---

