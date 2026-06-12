---
title: "Some init.d scripts not booting"
date: 2009-12-30
forum: General Help
---

### Post by mclark1129 on 2009-12-30
Hello,

I am having a problem where a script I have in my /etc/init.d folder is not running on boot.  When I initially created the script (which enables my wireless connection) and placed it in my init.d directory it worked great.  Now for some reason the script just doesn't seem to execute when the system boots.  When I log in I can manually execute the script and it works great, of course that's a big pain compared to it running automatically on start up.

Has anyone else had this problem before?  If so, what steps can I take to resolve it?

Here is script:

```
#! /bin/sh
# This script disables the ssb module and enables the wl module for
# wireless networking.

modprobe lib80211
insmod /lib/modules/`uname -r`/kernel/net/wireless/wl.ko
```

Thanks,

Mike

---

### Post by john newbuntu on 2009-12-30
Assuming you are not changing runlevels anywhere and using the default runlevel 2 at start, has this script been linked to /etc/rc2.d ? Is the original script under /etc/init.d owned by root and has executable bit set?

I would also suggest adding a simple command like:
logger "Running my script `date`"
at the beginning of the script and a similar logger command at its end.  This way, you can check in /var/log/syslog if the script is getting run.
You may also want to add a short sleep time in the end of the script like say: sleep 5

Another question is if the default "S20" prefix sufficient for you (in /etc/rc2.d) or should you promote/demote it up the order if there is a dependency.  Remember that K00 through K99 jobs are run first followed by S00 through S99.

In general, I would suggest using the "update-rc.d" to register your scripts with the System V style init process.

Another option is to add your script to /etc/rc.local but note that your script will the run absolutely last in the order.

---

### Post by sveinn on 2010-01-02
I register another instance of the same issue which I first noticed about 3 days ago with Karmic on a Dell Inspiron. 

Apache, Bluetooth and several other init.d processes fail to boot on start up. 

Have not attempted fix yet.

---

### Post by Leppie on 2010-01-02
if you're trying to run scripts at boot in karmic, it's using upstart.
scripts should be placed under /etc/init/
more info on upstart here: [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by mclark1129 on 2010-01-03
John,

I have not linked the script to /etc/rc2.d, but the script in /etc/init.d is owned by root and is executable.

After placing some logging statements within the script I've determined that it is just not being run during boot, as opposed to running but experiencing errors.  I have used "update-rc.d setup-wireless defaults" to register the scripts.  When I run the command again I get the following message:

update-rc.d: warning: /etc/init.d/setup-wireless missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/setup-wireless already exist.

I got the LSB warning when I initially ran update-rc.d as well, and when I researched the error it didn't to appear to be anything important.  

Like I said before, this was working great until just one day it randomly stopped.  I'm not sure if something like my runlevel has changed without me knowing.  When I run 'runlevel' from the command prompt the output is 'unkown'.  Is this a problem?  Also, how can I see what runlevels a script is registered for?

Leppie,

I tried moving the script to /etc/init/ with no success.

Thanks so much for the help,

Mike

---

### Post by mclark1129 on 2010-01-03
Correction,

My script DOES appear in /etc/rc2.d as S20setup-wireless, just in case that makes a difference.

Mike

---

### Post by mclark1129 on 2010-01-04
So it appears the problem is that my runlevel is appearing as 'unknown' instead of an actual runlevel.  As soon as I run "init 2" my wireless setup script runs and everything is great.  Now the problem is to figure out how to have the runlevel appear properly on boot, any suggestions?

---

### Post by tayran on 2010-02-08
I am having the same problem on a Kubuntu 9.10 (it was upgraded from 9.04 beta). After entering into KDE gui i see runlevel as unknown but it should be 2 instead.

When i run init 2 command then runlevel changes and all related startup scripts run as well. I found a difference in /proc/cmdline file which is as below:

root=UUID=9ab91724-2277-47c5-8fa5-c967286b9542 ro quiet splash

This is a little different then my other kubuntu installation. Can you check this value on your system?

---

### Post by Leppie on 2010-02-08
> **mclark1129 said:**
> Leppie,

I tried moving the script to /etc/init/ with no success.
just moving the script won't work. you'll need to modify it a bit, try something like this:
```
# disable ssb and wl modules
#
# This script disables the ssb module and enables the wl module for
# wireless networking.

description    "disable ssb and wl modules"

start on startup

task

script
    exec modprobe lib80211
    exec insmod /lib/modules/`uname -r`/kernel/net/wireless/wl.ko
end script

```

---

