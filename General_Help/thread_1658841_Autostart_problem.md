---
title: "Autostart problem"
date: 2011-01-03
forum: General Help
---

### Post by _Dert_ on 2011-01-03
Happy New year everybody! I have the following problem. I'm usuing clean installation of Ubuntu Server 10.10 with hlds on it. I can't get startup script for my hlds server to work, so i must lauch it always "by hands"... I have done these steps:

> nano etc/init.d/hlds.sh

with content:

> ### BEGIN INIT INFO
# Provides:          scriptname
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by deamon.
### END INIT INFO

#!bin/sh
cd /var/log/
echo "BEFOREFALL" >> ./syslog
cd /home/dert/hlds/
screen -A -m -d -S hlds1 ./hlds_run -binary ./hlds_i686 -game cstrike +map aim_map +ip 93.X.X.98 -pingboost 2 +exec server.cfg
echo "AFTERFALL55" >> /var/log/syslog

then given permission for it and added for autoload on startup

> sudo chmod +x /etc/init.d/hlds.sh
sudo update-rc.d hlds.sh defaults 99

When i lauch it as usual 

> sh /etc/init.d/hlds.sh or > sudo sh /etc/init.d/hlds.sh

Server launches and work normally, but it never launches on startup... Just wrotes BEFOREFALL and AFTERFALL55 into /var/log/syslog and that's all... Also tried using rc.local, but it never works too... In what can be the trouble? I think i checked all possible variants already...

---

### Post by matt_symes on 2011-01-03
Hi

If it runs when you type it manually but not when it is started by root using the run levels or /etc/rc.local then i would suggest it is some thing to do with your environment which is missing when run by root. Use full paths to everything and add any other variables it may need.

Kind regards

---

### Post by tredegar on 2011-01-03
I have had the same problem, with 10.04
It think it is because upstart still isn't working properly, and my script gets called before it should be.

My inelegant solution was to place a **sleep 40** as the first command in the script, so it is actually run later in the boot process, and then it works.

---

### Post by _Dert_ on 2011-01-03
**tredegar**

It worked with rc.local! Great idea, thank you!

And using it with init.d script not worked. I think it's because, don't know why, but these scripts are initialising after command *sudo shutdonw -r 0*, but _before_ phisycall reboot... that's the matter. Terrible system of upstart in Ubuntu 10.10... many manuals that i've seen now have to be modified...

Thanks, guys, for your help.

---

