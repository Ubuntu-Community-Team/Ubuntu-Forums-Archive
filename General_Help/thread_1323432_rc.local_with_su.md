---
title: "rc.local with su"
date: 2009-11-11
forum: General Help
---

### Post by atca on 2009-11-11
Hi

I'm trying to get opendchub to run at startup on 9.04 via /etc/rc.local

opendchub has been configured to run on port 411 which requires root or sudo to execute opendchub and allow it to bind.

My rc.local is as follows:

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
su root opendchub 
exit 0


However, this still doesn't start opendchub at start up.. running /etc/rc.local and entering the root password when prompted works, but the script doesn't seem to work at boot.

atca@atca-shuttle:~$ ls -l /etc/init.d/rc.local /etc/rc.local
-rwxr-xr-x 1 root root 788 2009-03-31 10:01 /etc/init.d/rc.local
-rwxr-xr-x 1 root root 285 2009-11-11 22:22 /etc/rc.local

Any thoughts?

---

### Post by sisco311 on 2009-11-11
the script runs as root at boot time, so you don't have to use su.

```
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
opendchub 
exit 0
```

btw, the correct syntax is *su root -c "command"* or simply *su -c "command args"*

---

### Post by atca on 2009-11-11
I've tried that already to no avail :( I've tried nearly every combo I can think of

---

### Post by atca on 2009-11-12
bump any help? I'm still no further.
 
Are there any logs I can check to see if rc.local is being called and if so why opendchub is failing to initialise / potentially failing to bind?

---

### Post by bodhi.zazen on 2009-11-12
Try using the full path to[FONT=monospace] [/FONT]opendchub in rc.local

You can run rc.local from a terminal

```
sudo /etc/rc.local
```

---

### Post by atca on 2009-11-12
I'll try using the full path tonight
 
sudo /etc/rc.local
 
prompts at the terminal for the sudo password, which when entered works and starts up opendchub, however rc.local on boot doesn't seem to work. 
 
This would suggest that the command is okay without the path, as manually sudo /etc/rc.local works, so why won't it work on boot?

---

### Post by Giblet5 on 2009-11-12
> **bodhi.zazen said:**
> **[COLOR="DarkRed"]Try using the full path to[FONT=monospace] [/FONT]opendchub in rc.local[/COLOR]**

You can run rc.local from a terminal

```
sudo /etc/rc.local
```

+1

When rc.local is being executed, there is no environment established (esp no PATH). You have to specify the whole pathname to any program run from boot scripts or from cron. Assuming that rc.anything will find programs via clairvoyance will end with unmet expectations. :)

---

### Post by atca on 2009-11-12
okay /etc/rc.local works via the terminal but still not at boot

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
#/usr/bin/opendchub 
exit 0

any ideas?
is rc.local invoked before the network interface comes up? i.e. could it be trying to bind to a network interface which has not been invoked / ready

---

### Post by bodhi.zazen on 2009-11-12
Now you have the command commented out

Remove the # from the line

> #/usr/bin/opendchub

rc.local is invoked last.

---

### Post by atca on 2009-11-12
sorry it's not commented out, that was a typo.

---

### Post by bodhi.zazen on 2009-11-13
The only other thing I can think of, what are the permissions of /etc/rc.local ?

you can confirm that it runs with a simple echo statement :

```
/usr/bin/opendchub                      & #Note the & to put opendchub in the background
echo "rc.local has run" > /root/rc.local.txt

exit 0
```

---

### Post by atca on 2009-11-13
thanks for your ongoing help

/etc/rc.local is as follows now

> #!/bin/sh -e
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
/usr/bin/opendchub &
echo "rc.local has run" > /root/rc.local.txt 
exit 0

there is no /root/rc.local.txt

would this be created even if opendchub fails to 'execute' i.e. if the script falls over at the opendchub line would it skip and output rc.local or would the script fall over straight away and exit, without even attempting to output rc.local.txt?

permissions for rc.local look ok to me as a novice.

> root@atcapollo-shuttle:/home/atcapollo# ls -l /etc/init.d/rc.local /etc/rc.local
-rwxr-xr-x 1 root root 788 2009-03-31 10:01 /etc/init.d/rc.local
-rwxr-xr-x 1 root root 333 2009-11-13 23:31 /etc/rc.local


i'm extremely baffled!

---

### Post by atca on 2009-11-13
p.s. what's the benefit of & in this scenario, the program has no gui and exists only in the terminal so I wouldn't expect "background" to do much, may be I misunderstand the concept?

---

### Post by sisco311 on 2009-11-13
> **atca said:**
> p.s. what's the benefit of & in this scenario, the program has no gui and exists only in the terminal so I wouldn't expect "background" to do much, may be I misunderstand the concept?

are you using karmic?

```
lsb_release -a
```

---

### Post by atca on 2009-11-13
nope 9.04 jaunty

> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty


---

### Post by sisco311 on 2009-11-13
it looks like /etc/rc.local is not executed at boot time.


what's the content of /etc/init.d/rc.local:
```
cat /etc/init.d/rc.local
```

oh and post the output of:
```
find /etc/ -iname "*rc.local"
```

---

### Post by atca on 2009-11-13
see 

> atcapollo@atcapollo-shuttle:~/xpad$ cat /etc/init.d/rc.local
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs
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


---

### Post by atca on 2009-11-13
and

> atcapollo@atcapollo-shuttle:~/xpad$ find /etc/ -iname "*rc.local"
/etc/rc3.d/S99rc.local
/etc/rc4.d/S99rc.local
find: &#8216;/etc/cups/ssl&#8217;: Permission denied
/etc/rc2.d/S99rc.local
find: &#8216;/etc/chatscripts&#8217;: Permission denied
/etc/init.d/rc.local
/etc/rc.local
find: &#8216;/etc/hamachi&#8217;: Permission denied
find: &#8216;/etc/ppp/peers&#8217;: Permission denied
/etc/rc5.d/S99rc.local
find: &#8216;/etc/ssl/private&#8217;: Permission denied


what does this do..
find /etc/ -iname "*rc.local"

---

### Post by atca on 2009-11-14
bump, any ideas as to why /etc/rc.local is not running /etc/init.d/rc.local looks fine from my limited experience

---

### Post by sisco311 on 2009-11-14
> **atca said:**
> 
what does this do..
find /etc/ -iname "*rc.local"

searches for the symbolic links in /etc/rc*.d

i.e.

if a symbolic link to /etc/init.d/rc.local is in the /etc/rc2.d directory (/etc/rc2.d/S99rc.local) then rc.local will be executed in runlevel 2.

everything looks fine; rc.local is executed at boot time, but 
#!/bin/sh **-e** means: exit immediately if any untested command fails.

*/usr/bin/opendchub* probably fails with an error and that's why
*echo "rc.local has run" > /root/rc.local.txt* is not executed.

so try to redirect the stderr and stdout of the command to a file and see if any error occurred:

```
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
/usr/bin/opendchub &> /root/rc.local.txt 
exit 0
```

---

### Post by atca on 2009-11-14
> **sisco311 said:**
> searches for the symbolic links in /etc/rc*.d

i.e.

if a symbolic link to /etc/init.d/rc.local is in the /etc/rc2.d directory (/etc/rc2.d/S99rc.local) then rc.local will be executed in runlevel 2.

everything looks fine; rc.local is executed at boot time, but 
#!/bin/sh **-e** means: exit immediately if any untested command fails.

*/usr/bin/opendchub* probably fails with an error and that's why
*echo "rc.local has run" > /root/rc.local.txt* is not executed.

so try to redirect the stderr and stdout of the command to a file and see if any error occurred:

```
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
/usr/bin/opendchub &> /root/rc.local.txt 
exit 0
```

using the rc.local quoted above, still no rc.local.txt is being created.. it doesn't look like its executing at all


```

root@:/home/# cd /root
root@:~# ls
tmp  xorg.conf.new

```

I'll retry with

```

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
/usr/bin/opendchub &
echo "rc.local has run" & 1>/root/rc.localout.txt 2>/root/rc.localerror.txt
exit 0

```

---

### Post by sisco311 on 2009-11-14
Does the daemon start with:
```
sudo /etc/init.d/rc.local start
```?

---

### Post by atca on 2009-11-14
yes it does

---

### Post by sisco311 on 2009-11-14
I noticed something interesting while playing with opendchub.

if i try to start it in a sub-shell, i get this:
```
sh /usr/bin/opendchub 
/usr/bin/opendchub: 1: ELF: not found
/usr/bin/opendchub: 2: Syntax error: word unexpected (expecting ")")

sh -e /usr/bin/opendchub 
/usr/bin/opendchub: 1: ELF: not found

```

but
```
sh -c opendchub
```works.

So try:
```
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
sh -c /usr/bin/opendchub 

exit 0
```

---

### Post by atca on 2009-11-14
the text file is now being created in /root/

but the opendchub is not running.. this is painful, I don't really see why it won't start.

it start when ruuning either

/etc/rc.local

or 

/etc/init.d/rc.local start

from the CLI

---

### Post by sisco311 on 2009-11-14
at least we know that rc.local is executed at boot time. :)

try to specify the working directory for opendchub and redirect the stderr and stdout to a file:
```
sh -c "/usr/bin/opendchub -w /root &> /root/error.log"
```

also check the log file created by the app: /root/.opendchub/log

---

### Post by atca on 2009-11-14
> #!/bin/sh -e
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
sh -c "/usr/bin/opendchub -w /root &> /root/error.log"
exit 0


and

> 
root@:/home/# ls /root/
rc.local.txt  tmp  xorg.conf.new


no /root/error.log and opendchub is not ruuning,  from CLI it still runs :(

---

### Post by atca on 2009-11-15
bump, any further ideas?

---

