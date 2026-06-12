---
title: "run scripts at boot - not working"
date: 2009-08-23
forum: General Help
---

### Post by cbear on 2009-08-23
I am trying to run two commands at boot (tuncfg and hamachi start)

Everything I read refers to /etc/rc.local to perform this task.

BUT, my brand new 9.04 ubuntu machine does not have that file in /etc.

My other 8.10 machines does have the file.

I need to run both of these commands as root. I created the file myself and added the following lines:

Code:

```
/usr/src/hamachi/tuncfg/tuncfg
/usr/src/hamachi/hamachi start
```

I made the file executable:


```
chmod +x rc.local
```


No dice, does not run at boot.

If I run the file manually after booting, it works fine and my hamachi starts and works perfect.

Why does rc.local not run at boot ?

---

### Post by unutbu on 2009-08-23
[list]
[*] Did you put
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
# By default this script does nothing.

exit 0
```

in your /etc/rc.local? Note that ```


/usr/src/hamachi/tuncfg/tuncfg
/usr/src/hamachi/hamachi start

```
should be placed before the 
```

exit 0
```

otherwise the commands will not get run.
[*] Do you have a script called /etc/init.d/rc.local ?
[list]
[*] If /etc/init.d/rc.local exists, check that /etc/rc2.d/S99rc.local is a symlink to /etc/init.d/rc.local
[list]
[*] If /etc/init.d/rc.local exists but you do not have /etc/rc2.d/S99rc.local then run
```
sudo update-rc.d rc.local defaults 99
```
This will create the symlink, so that rc.local is run at boot.
[/list]
[*] If /etc/init.d/rc.local does not exist, then post back. I believe Ubuntu is transitioning to using upstart (and away from /etc/init.d scripts) to control the boot process. I think I can show you how to use upstart to run the scripts.
[/list]
[/list]

---

### Post by cbear on 2009-08-23
actually, I don't have /etc/init.d/rc/local at all.  Did some research and it appears debian doesn't use that but instead calls for using /etc/init.d/local  (not rc.local).  Right now I have created /etc/init.d/local and I put these two lines (and nothing else)into that file:

```
/usr/src/hamachi/tuncfg/tuncfg
/usr/src/hamachi/hamachi start
```

Does Ubuntu support the use of rc.local ?  I was under the impression that it didn't.  Strange thing is, I have another 8.10 ubuntu machine and it DOES have an rc.local file.  The new machine I am working on now is a 9.04 ubuntu.

---

### Post by cbear on 2009-08-23
I looked at my other linux box that runs tuncfg and hamachi the same way I WANT to run on the new machine.  It has a script in /etc/init.d called 'hamachi' with the following:

```
#!/bin/sh
# tuncfg + hamachi

case "$1" in
'start')
	sudo tuncfg
	hamachi start
	;;
'stop')
	;;
*)
	echo "Usage: $0 { start | stop }"
	;;
esac
exit 0
```

I put the exact same script into the new machine.  Does not load.

I'm stumped :(

---

### Post by unutbu on 2009-08-23
Try running
```

sudo update-rc.d himachi defaults 99
```

This will make a symlink from /etc/rc2.d/S99himachi to /etc/init.d/himachi.

Note that things listed in /etc/rc2.d should get run at boot time. (/etc/init.d is a repository for boot scripts, but not all scripts in /etc/init.d get run at boot time.)

---

### Post by cbear on 2009-08-23
thanks.. I ran that and made the value for tuncfg 98 and hamachi 99 so that tuncfg would run first (as it needs to).  The command executed without error and created the links.  BUT, it does not run at boot.  tuncfg is running , I can see that from 

ps -ae | grep tuncfg

Although, it seems to run with or without the file in init.d.  Something else is loading tuncfg and I cannot figure out where or what is doing it.

As soon as the machine boots, I can run (manaully)

sudo hamachi start

and bang...it works.

All I want is "sudo hamachi start" to run at the end of boot so it occurs as late as possible.  This is the content of the hamachi file I created in /etc/init.d ...and I ran the "99" command you supplied.


```
# load hamachi at boot

case "$1" in
'start')
        hamachi start
        ;;
'stop')
        ;;
*)
        echo "Usage: $0 { start | stop }"
        ;;
esac
exit 0
```

---

### Post by slakkie on 2009-08-23
Set the PATH in your script.

which hamachi will tell you the location, and then you know enough

eg

/usr/bin/hamachi

Then your path becomes

PATH=/usr/bin

You can also do it like this

dirname $(which hamachi)

which prints out the dir location of your binary.

Or hardcode it.

---

### Post by cbear on 2009-08-23
I got it working finally. Took a slightly different route:

1. created a script /etc/init.d/hamtun
Code:

#!/bin/bash

# script to load tuncfg then hamachi at boot

sudo /usr/src/tuncfg/tuncfg
sudo /usr/src/hamachi/hamachi start

2.
Code:

chmod +x /etc/init.d/hamtun

3. execute this command to link the script to boot

Code:

update-rc.d hamtun defaults

4. reboot...and it works.

One note: tuncfg was loading all along, but not in the right order. If I remove the "tuncfg" line from this script and JUST load "hamachi start", it does not work because hamachi is being loaded before tuncfg. So, I suspect when I am loading tuncfg in this script it is getting loaded again elsewhere at boot - but that doesn't hurt anything.

Thanks all for the help!

---

### Post by slakkie on 2009-08-24
btw, scripts in init.d do not need to use sudo since they are executed as root already.

---

### Post by cbear on 2009-08-24
hmmm... I think you are right, but I just took the "sudo" out and rebooted and it does not work.  Put the sudo back in and it works again.  Makes sense though, init.d is already root.  Now I am curious :)

---

