---
title: "Ubuntu 9.04 reboot question"
date: 2010-11-15
forum: General Help
---

### Post by holly1 on 2010-11-15
I am running Ubuntu 9.04 on an LX-800 single board computer.  My goal is to run several processes upon startup.  I put the links to the startup scripts in the /etc/rc2.d directory (I know I'm in runlevel 2) and the startup scripts are in /etc/init.d.  Upon reboot the processes start ok (I can tell because I see the log files) but when I login and do a "ps -ef" i can see that they are no longer running.  When I start these processes using these same startup scripts after login, they run continuously as they should.  Has anyone ever seen this happen?  Any help would be appreciated!

---

### Post by tredegar on 2010-11-15
You don't say just what these processes are, but remember that some may need a 
resource (eg a GUI) or an environment that is not available to the user (usually root) that is running the scripts in **/etc/rc.d**, so they might start, but then fail.

If you told us what the processes are (and just what they do, if they are not standard linux processes) perhaps we can provide better help.

---

### Post by holly1 on 2010-11-15
The processes that I'm trying to run are custom - I wrote them for several different purposes, one to set the ip address, one to listen for udp messages, etc. But when I noticed that they all started and then died, I wrote a process that simply increments a counter and outputs it to a log file so that I could tell when it died.  Each time I rebooted it counted to a different number before it died, somewhere around 60,000.  Do  you think it has to do with privileges during bootup?

---

### Post by holly1 on 2010-11-17
I found the solution.  I need to added the daemon() system call at the beginning of each of the processes and that worked!  Thanks,

---

