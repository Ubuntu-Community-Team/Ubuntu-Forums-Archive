---
title: "Need some help writing a script of some sort"
date: 2009-11-05
forum: General Help
---

### Post by lordofduct on 2009-11-05
Hi, I'm not very knowledgeable in the whole boot scripts and the sort.

So I want to know if anyone can point me in the right direction for this.

All right so I have multiple xorg.conf files for several different things. There is a dualmonitor mode, a single monitor mode, default mode (no nvidia drivers or anything), and a vbox mode. This last one the most important... I sometimes boot up Ubuntu as a virtual machine off the physical drive while I'm in windows... it does NOT support the nvidia driver there so I need to use the vbox settings. But when I boot into Ubuntu directly, I want to use the dualmonitor configuration. And randomly I want the singlemonitor set up... sometimes.


So what I'm trying to do is this:

1) unload-script - a script that when I restart or turn of the computer the script copies the xorg.conf.default (minimal settings) to the xorg.conf file. This way the next time I boot up it functions no matter what (I tested the config, it works in all my configurations).


2) boot-script -

Now when booting, sometimes it will stop the boot process and wait for some input from the user... like in the case of errors or other crap. I want to know if I can do something similar, something that before gdm starts up and shows the login screen I can display a question and ask for an input... like:

bash:> Please select xorg configuration. Choices are 1, 2, 3, 4:

and I can choose between my modes. The script then just basically copies the corresponding xorg.conf.##### to the xorg.conf file, and starts up X and gdm and I go on like I want. It would be even cooler if there was a timeout that if I didn't make a choice it would just go to the xorg.conf.default (which always works).


Anyone have any ideas?


Really if anyone could tell me WHERE I'd put such scripts, I bet I could figure out the script itself.

---

### Post by doas777 on 2009-11-05
well you can put the script anywhere you want, since you will have to use sudo to run it anyway. I would probably put it in your /etc/X11/ just cause it's easy to keep organized. I think the "correct" place would be /usr/sbin/. not an expert on posix paths though.

your script shoudl be pretty easy so take a crack at it and let us know how it works!

---

### Post by Giblet5 on 2009-11-05
```
#!/bin/bash

PATH=/bin:/sbin:/usr/bin

echo "#########################################"
echo "#########################################"
echo 
echo "Enter the X session desired:"
  1 = nvidia
  2 = blah blah blah
"
/bin/echo -n "Your Selection: "

read value
case $value in
    1)
        cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf;;
    2)
        cp blah blah;;
    *)
        ;;
esac

exit 0
```

Make that do what you want, verify it, then insert the path of the script in the dostart() function of /etc/rc2.d/S30gdm as a foreground command.

Booting will pause until the question is answered.

You can make it pretty using "dialog" from the repositories.

---

### Post by lordofduct on 2009-11-05
Thanks Giblet5, you were very helpful.

This was the bash I adapted from your code and instruction:

```

#!/bin/bash

PATH=/bin:/sbin:/usr/bin

do_start () {
	echo "#########################################"
	echo "#########################################"
	echo "LoD XorgModePicker"
	echo "#########################################"
	echo
	echo "Enter the X session desired:
	  1 = default
	  2 = nVidiaSingleMonitor
	  3 = nVidiaDualMonitor
	  4 = vBoxDisplayManager
	"
	echo -n "Your Selection: "

	read -t 5 value
	case $value in
		1)
			cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf
			;;
		2)
			cp /etc/X11/xorg.conf.singlemon /etc/X11/xorg.conf
			;;
		3)
			cp /etc/X11/xorg.conf.dualmon /etc/X11/xorg.conf
			;;
		4)
			cp /etc/X11/xorg.conf.vboxman /etc/X11/xorg.conf
			;;
		*)
			cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf
			echo "you failed to make a choice... default was loaded."
			;;0
	esac
}

do_stop () {
	cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf
}

case "$1" in
	start|"")
		do_start
		;;
	restart|reload|fore-reload)
		# No-op
		;;
	stop)
		do_stop
		;;
	*)
		echo "Usage: xorgModePicker.lod.sh [start|stop]" >&2
		exit 3
		;;
esac

:

```

I ended up placing it in /etc/init.d and registering it via update-rc.d


sudo update-rc.d my_script defaults


It reverts back to default when stopped...

thanks again.

[edit1]

errr, little issue in that the splash screen is covering it up... I'll get this.

[edit2]

got it with this:

```

#!/bin/bash

PATH=/bin:/sbin:/usr/bin

. /lib/init/vars.sh
. /lib/init/splash-functions-base
. /lib/init/splash-functions0

do_start () {
	if [ "$VERBOSE" = no ]
	then
		splash_stop
	fi

	echo "#########################################"
	echo "#########################################"
	echo "LoD XorgModePicker"
	echo "#########################################"
	echo
	echo "Enter the X session desired:
	  1 = default
	  2 = nVidiaSingleMonitor
	  3 = nVidiaDualMonitor
	  4 = vBoxDisplayManager
	"
	echo -n "Your Selection: "

	read value
	case $value in
		1)
			cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf
			;;
		2)
			cp /etc/X11/xorg.conf.singlemon /etc/X11/xorg.conf
			;;
		3)
			cp /etc/X11/xorg.conf.dualmon /etc/X11/xorg.conf
			;;
		4)
			cp /etc/X11/xorg.conf.vboxman /etc/X11/xorg.conf
			;;
		*)
			cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf
			echo "you failed to make a choice... default was loaded."
			;;
	esac
}

do_stop () {
	cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf
}



case "$1" in
	start|restart|"")
		do_start
		;;
	reload|fore-reload)
		# No-op
		;;
	stop)
		do_stop
		;;
	*)
		echo "Usage: xorgModePicker.lod.sh [start|restart|stop]" >&2
		exit 3
		;;
esac

:

```

for some reason the time out I had before doesn't work when ran during boot up, but it does if ran once logged in (opening a terminal and running the script through /etc/init.d). Oh and I moved the priority up to 29 in the update-rc.d command so that it occurs just before gdm loads.

sudo update-rc.d my_script start 29 2 3 4 5 . stop 29 0 1 6 .

for anyone wondering, if you happen to write a similar script (you probably don't want exactly what I ended up with) you remove it with:

sudo update-rc.d -f my_script remove

the script has to be executable and in the /etc/init.d directory

---

### Post by lordofduct on 2009-11-07
So like a dingle berry I decided to upgrade to 9.10 today... why... I felt slightly masocistic today.

So everything is up and running and all... but this script failed to work.

I looked in the rc#.d folders and come to find out gdm is not listed in there. I even went as far as removing gdm with update-rc.d .... remove, and low and behold nothing gets removed because it's not in there.

Of course gdm still boots.

So I can't figure out which of these damn scripts is starting gdm... I put my script at 19 and boot with out the splash (so I don't even have to bother to check and stop it) and I'm not getting anything. I can't figure where to run the damn thing... isn't it if I run it to early that write options won't be initialized?

Any help would be greatly appreciated.

---

### Post by lordofduct on 2009-11-08
Well I get why it doesn't run. I've been reading that that the init process has been changed over to "Upstart" (no I don't know what it is exactly), which from what I read is an event based boot process. Looking through /etc/init I see that different applications have script configurations associated with them to start them up at specific events in the boot process. This way different scripts can run parallel (so I assume).

Explains why each time I boot in in verbose mode the gdm login screen appears at random points in the boot order process. Ok...

So now I need to locate a hole in here that I can latch into... but even so this whole input thing is more of a hack way of doing it.

grrrrrrrr

---

