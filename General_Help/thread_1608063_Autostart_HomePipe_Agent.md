---
title: "Autostart HomePipe Agent"
date: 2010-10-28
forum: General Help
---

### Post by tberman333 on 2010-10-28
HomePipe ([www.homepipe.net](www.homepipe.net)) a site that lets you access folders on your PC remotely just came out with a Linux client.

I have successfully installed this on my Ubuntu 10.10 machine and it seems to be working well.  My problem is, I can't figure out how to have the agent autostart when I boot.

Currently, to launch the agent, I need to open a terminal, change to the directory where the agent is installed, then run this command:

./HomePipeAgent -start &

I assume it should be fairly simple to add this to the Startup Applications, but being a noon I can't figure it out!

Thanks for the help!

---

### Post by ajgreeny on 2010-10-28
Thast is obviously a script file that is executed with the ./HomePipeAgent -start & command, so probably the easiest way to start it at session start is to make an executable script file in your home folder and save it as homepipe.sh, then point to it in **System >Preferences >Startup Applications**.

The script file will be:-
```
#!/bin/bash
/path/to/HomePipeAgent -start &

``` Give it a try and come back again if it doesn't work.

You may also find that a simplified bash command in the command box of **System >Preferences >Startup Applications** may work.  Try ```
bash -c "/path/to/HomePipeAgent -start &"
```in full with all the quotation marks as shown.  You could even try the path and command as you use in terminal, ie ```
/path/to/HomePipeAgent -start &
```but I don't think that will work without the **bash -c** prefix.

---

### Post by tberman333 on 2010-10-28
Thank you very much for your help.  It is a script in that file... here is what is in that file:

```
#!/bin/sh

# Shell wrapper for the HomePipe Linux Agent.
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:./lib
./HomePipe.AgentService.exe $@
```

When I create the homepipe.sh file like you suggested, I get a message that says:
```
/home/todd/homepipe/HomePipe/HomePipeAgent: 5: ./HomePipe.AgentService.exe: not found

```

Any thoughts on another way around this one?

Thanks again for the help!

EDIT - Note:
I see that the HomePipe.AgentService.exe is directly in the HomePipe folder, not in the Homepipe/lib/ folder... not sure if that is what the problem is, but thought I would point it out just in case.

---

### Post by ajgreeny on 2010-10-28
Sorry, but all that is beyond me; .exe files are windows executables, not for linux, so I don't know how to help you any more.

---

### Post by Squish42 on 2011-01-08
After a lot of trial-and-error, and working with the good people at HomePipe, here's what I did...

Be aware, this works on my 10.04 LTS install, your mileage may vary.

Also be aware, as I have this installed, HomePipe is running with root privileges.  I decided I'm OK with this.  

**Install HomePipe:**
Downloaded "HomePipe.tar.gz"
Copy the _contents_ of the untar'ed directory "HomePipe" into: /usr/local/homepipe
Set the login rights
```
cd /usr/local/homepipe
sudo ./HomePipeAgent

```
Note: Type your User & Pass very carefully.  The script records everything, even a Backspace.  But luckily, once it's set, it is set.

Do a Ctrl+C to stop the Agent then confirm settings with
```
sudo ./HomePipeAgent -start
```

**To make the Agent launch on reboot:**
Copy the following 'homepipe' script into /etc/init.d/

```

#!/bin/sh
# chkconfig: 345 20 80
# description: Starts the HomePipe Agent
# processname: HomePipeAgent

### BEGIN INIT INFO
# Provides:          homepipe
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start HomePipe processes at boot time
# Description:       Enable HomePipe service.
### END INIT INFO

# Location of this script file: /etc/init.d/homepipe

# Location of the HomePipe Agent files
BASEDIR=/usr/local/homepipe

if [ "`whoami`" != "root" ]; then
	echo "Must run as root"
	echo "Usage: sudo $0 {start|stop|restart|status}"
	exit 1
fi

prog="homepipe"

start() {
	# Check if the HomePipe Agent is already running
	if [ -z "$(pgrep HomePipe)" ]; then
		echo -n "Starting HomePipe Agent: "
		cd $BASEDIR
		./HomePipeAgent -start & 
		sleep 2
	else
		echo "HomePipe is already running"
		pgrep -l HomePipe
	fi
	return 0
}

stop() {
	echo -n "Stopping HomePipe Agent: "
	pkill HomePipe
	# RETVAL is set to 0 if pkill is successful, otherwise it is set to 1
	RETVAL=$?
	[ $RETVAL -eq 0 ] && echo "Stopped."
	[ $RETVAL -ne 0 ] && echo "Stop failed.  Possibly nothing to stop."
	echo
	return $RETVAL
}

restart() {
	stop
	start
}

status() {
	# Check if the HomePipe Agent is running
	if [ -z "$(pgrep HomePipe)" ]; then
		echo "HomePipe Agent is not running"
	else
		echo "HomePipe is running"
		pgrep -l HomePipe
	fi
	return 0
}


case "$1" in
start)
	start
	exit 0 
	;;
stop)
	stop
	exit 0
	;;
restart)
	restart
	exit 0
	;;
status)
	status
	exit 0
	;;
*)
	echo "Usage: sudo $0 {start|stop|restart|status}"
	exit 1
esac

```

Make sure the script is executable:
```
cd /etc/init.d/
sudo chown root:root homepipe
sudo chmod 755 homepipe

```

Then install init script links:
```
sudo update-rc.d homepipe defaults 98 02
```

Note: To _remove_ the script from startup, use:
```
"sudo update-rc.d -f homepipe remove"
```

To check to see if the Agent is running use:
```
sudo ps -A | grep "Home"
```

---

### Post by Squish42 on 2011-01-13
Something broke.  After the latest round of updates and a reboot, HomePipe did not automatically start on reboot.  Back to the drawing board.

---

### Post by tberman333 on 2011-01-13
> **Squish42 said:**
> Something broke.  After the latest round of updates and a reboot, HomePipe did not automatically start on reboot.  Back to the drawing board.

I was having problems too.  I think I am giving up on HomePipe anyway...  They changed their pricing structure and now only allow you to connect for free 10 times per month and it is not very reliable.  

I use Subsonic for music... now all I need is a good way to access my pictures and I will have everything I needed HomePipe for.

---

