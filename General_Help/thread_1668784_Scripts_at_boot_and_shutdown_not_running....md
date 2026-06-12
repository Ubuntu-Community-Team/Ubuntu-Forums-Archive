---
title: "Scripts at boot and shutdown not running..."
date: 2011-01-16
forum: General Help
---

### Post by OrnithO on 2011-01-16
Hi
I have a small but annoying problem... I have two scripts that I want to run automatically one at boot and one at shutdown.

For the one at boot I tried to put it in rc.local or to create a file in /etc/init.d/ based on the others files in the folder but nothing worked... :( I need it to run system-wide and not once a specific user is logged in.

For the script at shutdown I don't know how to do it but it can be user specific or system-wide I don't really care...

I am running Ubuntu 10.10 64bits with kernel 2.6.35-24-generic

If anyone has a solution, thanks.

PS. I should add that when executed manually both scripts works perfectly well and I don't need those script to run continuously in the background, just run and quit.

---

### Post by lithopsian on 2011-01-16
The files in init.d are not run at boot.  Some of them are linked from /etc/rcS.d (run for every boot) or rc2.d (run level two, normal X session).  You'll quickly see the links.  Add your script to init.d and a link to, perhaps rc2.d depending on when you want to run.

Scripts at shutdown are run from the links in rc0.d, and for reboot from rc6.d.

In most cases, adding some code in rc.local works, or calling another script.  This avoids polluting the expected links.  I'm not sure what happened to yours that it didn't run.  This part of the boot isn't very visible because your X session will already be started and the splash is gone.  Check that you have a link in rc2.d to run rc.local, usually S99rc.local to run near the end of the boot.  Check your paths and syntax.  Maybe start with something simple and visible.

---

### Post by OrnithO on 2011-01-16
> **lithopsian said:**
> 
In most cases, adding some code in rc.local works, or calling another script.  This avoids polluting the expected links.  I'm not sure what happened to yours that it didn't run.  This part of the boot isn't very visible because your X session will already be started and the splash is gone.  Check that you have a link in rc2.d to run rc.local, usually S99rc.local to run near the end of the boot.  Check your paths and syntax.  Maybe start with something simple and visible.
Well I didn't have any link in rc2.d so I added it and checked the permissions and all but I didn't worked... My splash is deactivated but I didn't see any errors during the boot process. In fact I didn't see anything about rc.local...
I also did put my script directly in rc2.d with S80 but didn't worked...

---

### Post by OrnithO on 2011-01-16
> **lithopsian said:**
> 
In most cases, adding some code in rc.local works, or calling another script.  This avoids polluting the expected links.  I'm not sure what happened to yours that it didn't run.  This part of the boot isn't very visible because your X session will already be started and the splash is gone.  Check that you have a link in rc2.d to run rc.local, usually S99rc.local to run near the end of the boot.  Check your paths and syntax.  Maybe start with something simple and visible.
Well I didn't have any link in rc2.d so I added it and checked the permissions and all but I didn't worked... My splash is deactivated but I didn't see any errors during the boot process. In fact I didn't see anything about rc.local...
I also did put my script directly in rc2.d with S80 but didn't worked...

Whoops sorry for the double answer...  Also I tried the method described on the wiki [here]("https://help.ubuntu.com/community/UbuntuBootupHowto#Installing custom init-scripts") but it didn't worked either...

---

### Post by lithopsian on 2011-01-17
I'm not sure what more I can add.  If you have a script in /etc/init.d, correctly linked from the runlevel you are using, permissions set, execute but set, then it will get run.  Otherwise your machine wouldn't boot at all.

You can try putting something trivial earlier in the boot sequence.  Maybe a log message and a sleep so you can see it pausing.  Or not!  Scripts often have trivial checks at the start which can cause them to exit if a certain file or executable isn't present, so make sure your rc.local isn't just exiting.

Also check which runlevel you are actually booting into.  Would be a shame to be putting links in rc2.d and booting at runlevel 3 :)  Normally Ubuntu would boot to runlevel 2, but maybe something weird is happening.  Levels 3, 4 and 5 are all more or less duplicates of 2 and you coud boot to any of them and not notice the difference.

---

### Post by OrnithO on 2011-01-17
> **lithopsian said:**
> Also check which runlevel you are actually booting into.  Would be a shame to be putting links in rc2.d and booting at runlevel 3 :)  Normally Ubuntu would boot to runlevel 2, but maybe something weird is happening.  Levels 3, 4 and 5 are all more or less duplicates of 2 and you coud boot to any of them and not notice the difference.
I'll try and do that but I'm not sure how to do it.. I can put a simple script with a log in each runlevel but is this the best solution?

---

### Post by lithopsian on 2011-01-17
I should have said how.  Just type runlevel in a terminal and it will tell you where you are.  It will show you the previous and current runlevels.  Typically the previous will be something like "n", just look at the number after it.

---

### Post by OrnithO on 2011-01-17
Ok I did it and the runlevel is 2, I don't understand... I think I am doing something wrong because even the simplest script in rc2.d does not run at boot...
I was also looking for alternate solutions and I found [here]("https://help.ubuntu.com/community/CronHowto#Advanced Crontab") that you can do it with cron using the options @reboot but it doesn't work either...

---

### Post by matt_symes on 2011-01-17
Hi

Have a read up on update-rc.d

[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

Kind regards

---

### Post by lithopsian on 2011-01-17
Post the contents of rc2.d (ls -l), including your link or the rc.local link.  And post the contents of the rc.local script, and also ls -l /etc/init.d/rc.local.

---

### Post by OrnithO on 2011-01-19
Hi, sorry for the delay
@matt_symes: Thanks for the link! Unfortunately I already read it and it seems coherent with what I have done... Perhaps I misread something I don't know.
@lithopsian:
here is what you wanted hopes this helps, but for me it seems fine...
```
ls -l /etc/rc2.d/
total 4
lrwxrwxrwx 1 root root  26 2010-12-06 09:38 K25vpnagentd_init -> /etc/init.d/vpnagentd_init
-rw-r--r-- 1 root root 677 2010-11-01 17:36 README
lrwxrwxrwx 1 root root  20 2010-11-29 18:52 S20fancontrol -> ../init.d/fancontrol
lrwxrwxrwx 1 root root  20 2010-11-29 18:52 S20kerneloops -> ../init.d/kerneloops
lrwxrwxrwx 1 root root  21 2010-12-13 00:21 S20libnss-ldap -> ../init.d/libnss-ldap
lrwxrwxrwx 1 root root  17 2010-12-25 23:30 S20logkeys -> ../init.d/logkeys
lrwxrwxrwx 1 root root  17 2010-12-28 20:22 S20postfix -> ../init.d/postfix
lrwxrwxrwx 1 root root  18 2010-12-26 13:14 S20rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  27 2010-11-29 18:52 S20speech-dispatcher -> ../init.d/speech-dispatcher
lrwxrwxrwx 1 root root  13 2010-12-05 00:57 S23ntp -> ../init.d/ntp
lrwxrwxrwx 1 root root  19 2010-11-29 18:52 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2010-11-29 18:52 S50pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  15 2010-11-29 18:52 S50rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  15 2010-11-29 18:52 S50saned -> ../init.d/saned
lrwxrwxrwx 1 root root  19 2010-11-29 18:52 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2010-11-29 18:52 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  14 2010-11-29 18:52 S75sudo -> ../init.d/sudo
lrwxrwxrwx 1 root root  26 2010-12-06 09:38 S85vpnagentd_init -> /etc/init.d/vpnagentd_init
lrwxrwxrwx 1 root root  24 2010-11-29 18:52 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  17 2011-01-13 02:59 S95preload -> ../init.d/preload
lrwxrwxrwx 1 root root  22 2010-11-29 18:52 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2010-11-29 18:52 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root  18 2010-11-29 18:52 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  13 2011-01-17 01:44 S99rc.local -> /etc/rc.local
lrwxrwxrwx 1 root root  20 2011-01-17 21:18 S99touchpad -> /etc/init.d/touchpad

```
For rc.local I'm not exactly sure which one you are talking about /etc/rc.local or /etc/init.d/rc.local so here is both but from what I've read it isn't recommended to modify the content of /etc/init.d/rc.local:
```
ls -l /etc/rc.local 
-rwxr-xr-x 1 root root 362 2011-01-17 01:51 /etc/rc.local

```
```
Content of /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
#Touchpad two fingers scroll
sh /etc/default/touchpad.sh
exit 0
```
```
ls -l /etc/init.d/rc.local 
-rwxr-xr-x 1 root root 801 2010-12-26 12:14 /etc/init.d/rc.local

```
```
Content of /etc/init.d/rc.local
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
```

---

### Post by lithopsian on 2011-01-19
Your setup looks normal.  You would generally modify /etc/rc.local which is executed by /etc/init.d/rc.local when a symlink to it is present.  You have done this.  You can test the whole combo by typing sudo /etc/rc2.d/S99rc.local start.  "start" is the parameter that will be passed when your are booting the system.  At shutdown, it will be "stop".

Are you positive that /etc/rc.local is not getting executed at boot?  Did you test it with something visible earlier in the boot process?  Like S10rc.local with a log message and a sleep (and don't boot quiet)?  Although you can get output at a real boot, it is run after Gnome starts (except I see no S30gdm?) so you will never see it.  I really think S99rc.local is at least getting kicked off.

If it is actually being run but not working then I suspect you have a timing issue.  The commands you have added are being executed at the same time as X is trying to initialise.  They may be ignored, overwritten, or corrupted.  Try executing them after a long sleep and see if that does anything.

Does xinput really need to be run as root?  I would have thought it would be best to run it as yourself?  Maybe not, but if so then it should not be in rc.local but in your desktop manager autostart script.

---

### Post by OrnithO on 2011-01-21
Hurray, it worked!!! \\:D/
I don't know exactlya what I did but I rewritted the rc.local script and the link in init.d with S99 and it worked, I had another problem because xinput didn't found the X display so
```
sleep 45
export DISPLAY=:0.0
```
solved the matter. I was also able to add my backup script correctly.

Thanks a lot for your help!!! :D

Nb. I decided to run it during the boot process as root and not with the session because I have four sessions on my computer and it is the same for my backup script and I also need to implement the backup script on my father's computer which has several sessions on it too...

---

### Post by jwdonal on 2011-04-02
Hello all.  I thought I would share my experiences with startup scripts not running at boot.  My experience was the same as OrnithO, that is, I did every single trick, followed every single instruction to the letter, yet _nothing_ that I did would get the rc.local script to run at boot.  And just FYI, this was an almost raw install of Ubuntu 10.10 (Alternate x64).

I read the entirety of this thread and thought the last post by OrnithO was quite interesting.  He essentially said that he just "re-wrote" the rc.local file.  This gave me an idea that resulted in the rc.local script properly running at startup.  And I really think this must be a bug in the base file system install or something (you'll see why). Here is what I did:

```
# mv /etc/init.d/rc.local /root/
# update-rc.d rc.local remove
# mv /root/rc.local /etc/init.d/
# update-rc.d rc.local defaults
```I then rebooted the machine and BAM everything in /etc/rc.local ran like it was supposed to.  I literally spent 2 days trying to figure this out and get it working and ultimately I just had to remove and re-add the /etc/init.d/rc.local script using update-rc.d.  This is really weird.  But I certainly hope this post saves someone from 2 days of troubleshooting.  And maybe an ubuntu developer will see this and fix a bug or something...

Pz!

Jonathon

---

