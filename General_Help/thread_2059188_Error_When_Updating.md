---
title: "Error When Updating"
date: 2012-09-17
forum: General Help
---

### Post by Hungry Man on 2012-09-17
Fetched 2,185 kB in 2s (785 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up resolvconf (1.63ubuntu16) ...
/etc/init.d/resolvconf: 1: /etc/init.d/resolvconf: description: not found
/etc/init.d/resolvconf: 3: /etc/init.d/resolvconf: pre-start: not found
/etc/init.d/resolvconf: 5: /etc/init.d/resolvconf: end: not found
/etc/init.d/resolvconf: 7: /etc/init.d/resolvconf: Syntax error: "(" unexpected
invoke-rc.d: initscript resolvconf, action "start" failed.
dpkg: error processing resolvconf (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.4) ...
Killed (core dumped)
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 137
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc (= 1.99-21ubuntu3.4); however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 resolvconf
 grub-pc
 grub2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Hungry Man on 2012-09-17
Ideas?

---

### Post by wojox on 2012-09-17
You tried the usual?
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Hungry Man on 2012-09-17
>  sudo dpkg --configure -a
Setting up grub-pc (1.99-21ubuntu3.4) ...
Killed (core dumped)
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 137
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc (= 1.99-21ubuntu3.4); however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-pc
 grub2
root@colin-ubuntu:/home/colin# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up resolvconf (1.63ubuntu16) ...
/etc/init.d/resolvconf: 1: /etc/init.d/resolvconf: description: not found
/etc/init.d/resolvconf: 3: /etc/init.d/resolvconf: pre-start: not found
/etc/init.d/resolvconf: 5: /etc/init.d/resolvconf: end: not found
/etc/init.d/resolvconf: 7: /etc/init.d/resolvconf: Syntax error: "(" unexpected
invoke-rc.d: initscript resolvconf, action "start" failed.
dpkg: error processing resolvconf (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.4) ...
Killed (core dumped)
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 137
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc (= 1.99-21ubuntu3.4); however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 resolvconf
 grub-pc
 grub2
E: Sub-process /usr/bin/dpkg returned an error code (1)

Doesn't' seem to be working.

---

### Post by Hungry Man on 2012-09-17
Strange. Can't get it working.

---

### Post by Bashing-om on 2012-09-17
Hungry Man;
Is your network working ? If so ... 
 I do not claim to be the sharpest tack in the box. Looking at the output and the errors, It seems to me that there are 2 problems.
  Not happy with grub, and some faults IRT /etc/init.d/resolvconf (networking).
Not knowing how your system is set up ..I will assume a basic install and if this were my system I would try this:
fix grub:
```
sudo update-grub
```then replace the resolvconf file:
boot up your current version live cd and copy the file in the live cd to a usb thumb drive (or similar)
```
cp /etc/init.d/resolvconf /sdb1/resolvconf
```then in my current install
```
cp /etc/init.d/resolvconf /etc/init.d/resolvconf-orig
cp /sdb1/resolvconf /etc/init.d/resolvconf
```now see what happens with updates
```
sudo apt-get update
```if at this point all went well ... I would still be somewhat concerned about file corruption and would force a file check the easy way:
```
sudo touch /forcefsck
sudo shutdown -r now
```I would not be offended if others gave approval/comments on this recommendation.[INDENT][INDENT]hth <==BDQ
 
[/INDENT][/INDENT]

---

### Post by Hungry Man on 2012-09-18
My networking words fine. update-grub comes up with

Killed (core dumped)

---

### Post by f8l_0e on 2012-09-18
How are your partitions set up? One drive, multiple drives? GPT (efi) or MBR? LVM or regular partitions. What filesystems? Single OS or multiple?  If grub installation is crashing, it is either not liking information it is pulling from one of your drives or one of the grub configuration files.

---

### Post by Bashing-om on 2012-09-18
Hungry Man;
 In addition to f8l_0e's request. Did you copy the resolvconf file with a known good source (from the install cd  was my suggestion) ? See if we can not get this sloppyation figured out.

there is a bunch to think about!
sysop1@1204-a:~$ sudo find / -name "resolvconf"
[sudo] password for sysop1: 
/run/resolvconf
/etc/dhcp/dhclient-enter-hooks.d/resolvconf
/etc/resolvconf
/etc/network/if-down.d/resolvconf
/etc/bash_completion.d/resolvconf
/etc/init.d/resolvconf
/lib/resolvconf
/usr/share/lintian/overrides/resolvconf
/usr/share/doc/resolvconf
/sbin/resolvconf

[INDENT][INDENT]BDQ 
[/INDENT][/INDENT]

---

### Post by f8l_0e on 2012-09-18
I think Bashing-om might be on to something with your broken /etc/init.d/resolvconf file.

If the grub2 configuration parses that file, and is not in the proper format, I would imagine that would cause the installer to crash.

---

### Post by Hungry Man on 2012-09-18
> description "dnscrypt-proxy startup script"

pre-start script
    mkdir -p /run/dnscrypt
end script

start on (local-filesystems and net-device-up IFACE=lo)
stop on runlevel [!2345]

exec /usr/sbin/dnscrypt-proxy -a=127.0.0.2 --edns-payload-size=4096 --pidfile=/run/dnscrypt-proxy.pid --resolver-port=443 --user=dnscrypt --local-port=53 --tcp-only
That's what my resolvconf shows.

---

### Post by Bashing-om on 2012-09-18
On research ...all are packages (resolvconf, grub-pc and grub2) and dpkg is not happy.
As they are packages ...apt-get to the rescue ?
```
sudo apt-get install --reinstall resolvconf
sudo apt-get install --reinstall grub-pc
sudo apt-get install --reinstall grub2-common
```Can see nothing but good in trying this & see what results. ==> BDQ

---

### Post by f8l_0e on 2012-09-18
That's been modified, did you intend to setup dnscrypt-proxy?  That text you pasted is supposed to be in /etc/init/dnscrypt-proxy.conf  as per [http://insanitybit.wordpress.com/tag/dnscrypt/]("http://insanitybit.wordpress.com/tag/dnscrypt/").

The following the contents of my /etc/init.d/resolvconf

```
#!/bin/sh -e
# upstart-job
#
# Symlink target for initscripts that have been converted to Upstart.

set -e

INITSCRIPT="$(basename "$0")"
JOB="${INITSCRIPT%.sh}"

if [ "$JOB" = "upstart-job" ]; then
    if [ -z "$1" ]; then
        echo "Usage: upstart-job JOB COMMAND" 1>&2
	exit 1
    fi

    JOB="$1"
    INITSCRIPT="$1"
    shift
else
    if [ -z "$1" ]; then
        echo "Usage: $0 COMMAND" 1>&2
	exit 1
    fi
fi

COMMAND="$1"
shift


if [ -z "$DPKG_MAINTSCRIPT_PACKAGE" ]; then
	ECHO=echo
else
	ECHO=:
fi

$ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"

# Only check if jobs are disabled if the currently _running_ version of
# Upstart (which may be older than the latest _installed_ version)
# supports such a query.
#
# This check is necessary to handle the scenario when upgrading from a
# release without the 'show-config' command (introduced in
# Upstart for Ubuntu version 0.9.7) since without this check, all
# installed packages with associated Upstart jobs would be considered
# disabled.
#
# Once Upstart can maintain state on re-exec, this change can be
# dropped (since the currently running version of Upstart will always
# match the latest installed version).

UPSTART_VERSION_RUNNING=$(initctl version|awk '{print $3}'|tr -d ')')

if dpkg --compare-versions "$UPSTART_VERSION_RUNNING" ge 0.9.7
then
    initctl show-config -e "$JOB"|grep -q '^  start on' || DISABLED=1
fi

case $COMMAND in
status)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    $COMMAND "$JOB"
    ;;
start|stop)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    if status "$JOB" 2>/dev/null | grep -q ' start/'; then
        RUNNING=1
    fi
    if [ -z "$RUNNING" ] && [ "$COMMAND" = "stop" ]; then
        exit 0
    elif [ -n "$RUNNING" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    elif [ -n "$DISABLED" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    fi
    $COMMAND "$JOB"
    ;;
restart)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the stop(8) and then start(8) utilities,"
    $ECHO "e.g. stop $JOB ; start $JOB. The restart(8) utility is also available."
    if status "$JOB" 2>/dev/null | grep -q ' start/'; then
        RUNNING=1
    fi
    if [ -n "$RUNNING" ] ; then
        stop "$JOB"
    fi
    # If the job is disabled and is not currently running, the job is
    # not restarted. However, if the job is disabled but has been forced into the
    # running state, we *do* stop and restart it since this is expected behaviour
    # for the admin who forced the start.
    if [ -n "$DISABLED" ] && [ -z "$RUNNING" ]; then
        exit 0
    fi
    start "$JOB"
    ;;
reload|force-reload)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the reload(8) utility, e.g. reload $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
    exit 1
esac
```

---

### Post by Hungry Man on 2012-09-18
When I was setting up DNSCrypt I messed around a lot. I probably broke resolveconf when I was trying to get it to work and before I'd figured out the proper way.

None of the reinstalls work. Same errors.

I replaced my resolve.conf with the one you posted. Now I get this.

> Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up grub-pc (1.99-21ubuntu3.4) ...
Killed (core dumped)
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 137
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc (= 1.99-21ubuntu3.4); however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 grub-pc
 grub2
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Bashing-om on 2012-09-18
that looks to have fixed the resolvconf prob....
on to grub-pc and grub2...... still think we need to replace them. How 'bout a 2 step process then as the 1 step did not do it.
suggest we try this approach:
```
sudo apt-get --purge remove grub-pc
sudo apt-get install grub-pc 
```see what changes before we cope with grub2.
[INDENT]regards <== BDQ
[/INDENT]

---

### Post by Hungry Man on 2012-09-18
I tried that and rebooted. Got a black screen. Booted into a livecd and used boot-repair and now I can boot up again.

When I try to install grub-pc I get

>  &#9474; You chose not to install GRUB to any devices. If you continue, the boot   &#9474;  
 &#9474; loader may not be properly configured, and when this computer next        &#9474;  
 &#9474; starts up it will use whatever was previously in the boot sector. If      &#9474;  
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474;  
 &#9474; unable to load modules or handle the current configuration file.          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you are already using a different boot loader and want to carry on     &#9474;  
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474;  
 &#9474; boot loader, then you should continue anyway. Otherwise, you should       &#9474;  
 &#9474; install GRUB somewhere.                                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Continue without installing GRUB? 

---

### Post by Bashing-om on 2012-09-18
we are looking good ! ok ..Go ahead and install grub-pc ... when done tell kernel where you want it:
```
sudo grub-install /dev/sdX
```where "X" is the disk drive (as in sda).

fingers crossed

---

### Post by Hungry Man on 2012-09-18
sudo grub-install /dev/sda
Killed (core dumped)

---

### Post by f8l_0e on 2012-09-18
So we are back to needing to know about your drives, partitions, mbr or gpt, and filesystems.

---

### Post by Hungry Man on 2012-09-18
What do you need to know/ how can I get you that information?

---

### Post by Bashing-om on 2012-09-18
I'll get to the methods to acquire the info directly... still looking as to why the kernel is unhappy ........please look and see if the kernel dumped a log file in your home directory named "core". If so, that file (if I can read it even) may tell us why kernel not happy.


[INDENT][INDENT][INDENT]BDQ
[/INDENT][/INDENT][/INDENT]

---

### Post by f8l_0e on 2012-09-19
A dumped core file isn't human readable, it is the contents of system memory at the time of the crash.  If the file is there you need gdb (The GNU Debugger) to run a backtrace to see what the program's last instructions were when it crashed.  You might also need the debugging symbols for the package that is crashing.  

You might need to run ```
ulimit -c unlimited
``` from the terminal immediately followed by the ```
apt-get sudo grub-install /dev/sda
``` to allow dump files over a certain size.

---

### Post by Bashing-om on 2012-09-19
f8l_0e's post is valid ...I been doing homework too.

Intellectual pursuit of cause. => Kernel is not happy.
so...we know can not replace grub-pc at this time. Does grub-pc depend on grub2 as a component of grub2-common.

How about we try and replace grub2 with:
```
sudo apt-get --purge remove grub2-common
sudo apt-get install grub2-common
```see if that takes and then try to replace grub-pc ?

BDQ

---

### Post by f8l_0e on 2012-09-19
I just had a thought.  Does your motherboard have BIOS setting to disable writing to the MBR? In fact, what model of motherboard is it?  If the MBR writing is being disabled by the BIOS that might screw up grub.

---

### Post by Hungry Man on 2012-09-19
sudo apt-get install grub2-common


That seems to have fixed it.

---

### Post by Bashing-om on 2012-09-19
well well well ...will wonders never cease !

There just aint no substitute for logic. Glad it works for ya.

 Please mark this thread as solved ...for others looking. Thanks to f8l_0e for the insight.

[INDENT]Just trying to do my little bit ==> BDQ

[/INDENT]

---

### Post by f8l_0e on 2012-09-19
Good job Bashing-om.  Thank you for the recognition, even though you found the fix.  It seems lately that some of the newer Linux guys are not as friendly as some of the older users.  It's was nice working together for a resolution.

---

### Post by Bashing-om on 2012-09-19
Thanks too... This is my operating system of choice ....and each day is a learning process.
And yeah I too am "old school". Using/learning computers was different back then for sure.

[INDENT][INDENT][INDENT]enjoyn' ubuntu ==>BDQ
[/INDENT][/INDENT][/INDENT]

---

