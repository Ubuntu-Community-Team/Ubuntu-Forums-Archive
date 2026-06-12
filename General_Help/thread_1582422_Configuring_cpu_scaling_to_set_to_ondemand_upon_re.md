---
title: "Configuring cpu scaling to set to ondemand upon reboot"
date: 2010-09-26
forum: General Help
---

### Post by l0uismustdie on 2010-09-26
Hello, I know that this has been a frequent discussion post and I have read a large portion of the posts but none of them have fixed this problem for me.  My computer seems to default to performance upon reboot (and yes I have waited the 60 seconds it should take to switch to ondemand).  I have tried a number of the ideas posted throughout the web but have been unable to set the default upon reboot.  Here is my current /etc/init.d/ondemand script:
```

### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

    for CPUFREQ in /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done
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

Also it seems like there should be something in here for cpu1 (since I am running a dual core machine).  I have tried creating scripts to run at start that would do the following
```

echo ondemand /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```

This hasn't worked either.  Anyone have any other suggestions for this problem?

---

### Post by prshah on 2010-09-26
> **l0uismustdie said:**
> /etc/init.d/ondemand script:
```

    start)
        start-stop-daemon --start --background --exec [color=red]/etc/init.d/ondemand background[/color]
        ;;


```


You seem to be missing a "--" (end of all parameters indicator), eg the part in red SHOULD read```
start-stop-daemon --start --background --exec [color=red]/etc/init.d/ondemand [color=blue]--[/color] background[/color]
```

---

### Post by l0uismustdie on 2010-09-26
Right...this is actually something I changed per one of the forums I previously read that explained this might be a mistake in the script.  Regardless with or without the "--" before "background" the default isn't set to ondemand upon reboot.

---

### Post by l0uismustdie on 2010-09-28
Just bumpin

---

### Post by l0uismustdie on 2010-10-15
Just thought I would bump this again...anyone out there?

---

### Post by mc4man on 2010-10-15
well for core2duo here it's
```
for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

If after booting and set (I presume) to performance, does this set to ondemand after 60 secs or so

```
sudo /etc/init.d/ondemand start
```
If it does then for some reason the script isn't called, if it doesn't then possibly  something wrong w/ your script.
(there's a strange mix of space and tab indents (4/8 space) - not sure if they matter here or not

---

### Post by Rumpty on 2010-10-15
For what it&#347; worth, In Meerkat, here is my ondemand file, which does run the CPU in Ondemand state. Im using an AMD dual core cpu.

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
	sleep 60 # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done
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

---

### Post by l0uismustdie on 2010-10-17
Well I updated to 10.10 hoping to resolve this problem but no luck there.  I changed the ondemand file to contain cpu*
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

    for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done
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
It looks like if I run
```

sudo /etc/init.d/ondemand start

```
I am able to switch to ondemand.  Anyone have any idea why the script isn't doing this or isnt running.   Just in case this will help at all here is a ls -l of my ondemand script
```

-rwxr-xr-x 1 root root  882 2010-10-17 02:59 ondemand

```

---

### Post by l0uismustdie on 2010-10-29
Anyone out there?

---

### Post by dcstar on 2010-10-29
> **l0uismustdie said:**
> Hello, I know that this has been a frequent discussion post and I have read a large portion of the posts but none of them have fixed this problem for me.  My computer seems to default to performance upon reboot (and yes I have waited the 60 seconds it should take to switch to ondemand).


All systems are set to Performance when booted, that is built into the kernel. The script is there to change things 60 seconds after booting.

If the script is not being run, then quite probably something before that script is not exiting properly and allowing that particular script to finally run.

What "improvements" have **you** made to the standard Ubuntu install?

---

### Post by l0uismustdie on 2010-10-30
Well I am assuming what you mean by "improvements" in this context is scripts that are running at the same runtime level as the ondemand script.  So, here are those scripts:
```

***@^^^:/etc/rc5.d$ ls
README           S20nfs-kernel-server  S50saned           S99acpi-support
S20boinc-client  S20speech-dispatcher  S70dns-clean       S99grub-common
S20fancontrol    S20winbind            S70pppd-dns        S99laptop-mode
S20gdomap        S25bluetooth          S75sudo            S99ondemand
S20kerneloops    S50pulseaudio         S90binfmt-support  S99rc.local
S20lpd           S50rsync              S91apache2

```

---

### Post by prshah on 2010-10-31
> **l0uismustdie said:**
> 
```

***@^^^:/etc/rc5.d$ ls
README           S20nfs-kernel-server  S50saned           S99acpi-support
[color=red]S20boinc-client[/color]  S20speech-dispatcher  S70dns-clean       S99grub-common

```

Correct me if I'm wrong, but isn't boinc-client a client for distributed computing? Have you signed up for any boinc projects? That is probably what is preventing CPU downscaling... I guess.

---

### Post by l0uismustdie on 2010-10-31
Interesting point.  I checked into it by first disabling the client so it wasn't booted at runtime and also investigating some of the preferences in the client.  It doesn't look like this should be affecting the ondemand script.

---

### Post by l0uismustdie on 2010-11-07
bump?

---

### Post by l0uismustdie on 2010-11-20
Bumping this one again

---

### Post by dcstar on 2010-11-20
> **l0uismustdie said:**
> Well I am assuming what you mean by "improvements" in this context is scripts that are running at the same runtime level as the ondemand script.
........

No, I mean what non-standard things have **you** done to your Ubuntu system to possibly "improve" things?

---

### Post by mc4man on 2010-11-20
A few things in what you've posted seem a bit curious in that you wonder why.
One is you keep mentioning the need to edit the ondemand script, any instance of that I've seen since 9.04>10.10 it's never been written (that one line),  as you've posted (pre-edit), so I wonder where it's coming from.

Also I've several laptops here where ondemand always starts and again I don't see S99laptop-mode in any rc* dir. (nor do I have laptop-mode-tools installed

---

### Post by l0uismustdie on 2010-12-30
Bump???

---

### Post by l0uismustdie on 2011-01-28
Anyone??

---

### Post by Sam Lars on 2011-02-03
Speaking of laptop mode, you should check your laptop mode settings. One of those settings tells it what CPU governor should be used in different situations.
Since evidently the /etc/init.d/ondemand script works, you could try telling it to write a file or something as well as the echo command just to confirm that it's running when it should.

---

### Post by l0uismustdie on 2011-02-05
Well it looks like everyone is hating laptop-mode-tools...and I don't know how or why it's on my machine.  So, I removed that.  

Additionally I tried writing the echo line to a file but it isn't writing.  The other thing I tried was actually executing the ondemand script from the rc directory and that still doesn't even change the scaling governor.

---

### Post by philinux on 2011-02-05
```
gksudo gedit /etc/init.d/ondemand
```

Line 27 reads "echo -n ondemand > $CPUFREQ"

Change ondemand to what you want say performance.

Save the file.

```
sudo update initramfs -u
```

Reboot to check.

---

### Post by l0uismustdie on 2011-02-05
What I want is ondemand... The governor is stuck in performance mode and I am looking to boot into ondemand mode.

---

### Post by Sam Lars on 2011-02-09
A couple things...
You have the ondemand option listed from this command, right?
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
And you have lower frequency options from this command?
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```
Just want to double check that it's possible.

When you run the script (or try to manually echo ondemand) does it give you any errors?

---

### Post by l0uismustdie on 2011-02-11
Well I think I've just about gotten to the bottom of this problem.  It looks like I don't have the proper permission to write to the scaling_governor
```

***@***:/sys/devices/system/cpu/cpu0/cpufreq$ ls -l | grep scaling_governor 
-rw-r--r-- 1 root root 4096 2011-02-11 12:16 scaling_governor

```When I changed the mods to 666 I was able to echo ondemand to the scaling_governor and this changed the frequency.  However, upon reboot it looks like these permissions get reset.  Does anyone know how I can change them and make them stick to what I change?

---

### Post by Sam Lars on 2011-02-12
My permissions look the same here:
```
ls -l | grep scaling_governor
-rw-r--r-- 1 root root 4096 2011-02-12 13:07 scaling_governor
```
If you're using sudo with your echo commands you should have no problem. If it's giving a permission error, you can try this:
```
sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor"
```

---

### Post by l0uismustdie on 2011-02-13
That does seem to work but brings me back to my original issue of what the ondemand script isn't actually setting the scaling_governor to ondemand...

Just for clarity here is my script again
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

    for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done
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

### Post by prshah on 2011-02-14
> **l0uismustdie said:**
> That does seem to work but brings me back to my original issue of what the ondemand script isn't actually setting the scaling_governor to ondemand...

Can you post back the output of the following terminal command```
ls -l `locate ondemand`
```

This will help us see if the ondemand script is correctly linked in each runlevel.

---

### Post by l0uismustdie on 2011-02-14
Very cool:
```

ls -l `locate ondemand`
-rwxr-xr-x 1 root root 882 2011-02-05 12:11 /etc/init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-07-16 15:41 /etc/rc2.d/S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-07-16 15:41 /etc/rc3.d/S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-07-16 15:41 /etc/rc4.d/S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-07-16 15:41 /etc/rc5.d/S99ondemand -> ../init.d/ondemand
-rw-r--r-- 1 root root  40 2010-11-10 09:46 /var/lib/update-rc.d/ondemand

```

I've never used the ``'s before what is the purpose of them in this command??

---

### Post by prshah on 2011-02-16
> **l0uismustdie said:**
> 
I've never used the ``'s before what is the purpose of them in this command??

The `` (reverse single quote) is used to "escape" to the shell within the command. Eg, in this case, the command ls -l gets parameters from the locate command (within ``).

An equivalent would be ```
ls -l  /etc/init.d/ondemand /etc/rc2.d/S99ondemand /etc/rc3.d/S99ondemand /etc/rc4.d/S99ondemand /etc/rc5.d/S99ondemand 
/var/lib/update-rc.d/ondemand
```

Another example, to see the ondemand source code for the currently running kernel```
cat /usr/src/linux-headers-`uname -r`/include/config/cpu/freq/gov/ondemand.h
``` Note how the current running version of the kernel is included by the uname -r command

Back to your problem, ondemand setup looks fine. Don't know why your's doesn't seem to work.

---

### Post by l0uismustdie on 2011-02-18
Very cool.  Thanks!

Anyone else have any ideas about this ondemand situation though?

---

### Post by vickoxy on 2011-04-01
Try this:
[http://wiki.ubuntuusers.de/Prozessortaktung#Hintergrundinfos-und-Einstellung-im-Terminal](http://wiki.ubuntuusers.de/Prozessortaktung#Hintergrundinfos-und-Einstellung-im-Terminal)

---

### Post by d3v1150m471c on 2011-04-01
I added this to /etc/rc.local and it works like a charm:
```

# Set full cpu frequency
SET_CPU() {
        cpufreq-selector -f 1600000
                }

SET_CPU

```

---

