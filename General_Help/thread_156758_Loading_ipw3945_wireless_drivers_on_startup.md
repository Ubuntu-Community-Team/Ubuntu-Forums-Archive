---
title: "Loading ipw3945 wireless drivers on startup"
date: 2006-04-07
forum: General Help
---

### Post by RiffX on 2006-04-07
Hello,

I wonder if some kind person could help me?

I'm running Ubuntu Breezy 5.10 on a Sony Vaio FE11S laptop, and I'm trying to configure my Intel ipw3945 wireless LAN driver to load when my laptop starts up. I've followed Intel's installation instructions.

The Install document is available [here]("http://ipw3945.sourceforge.net/INSTALL").

When I boot up, the wireless connection is not found at all. I can MANUALLY load the driver by navigating to the install directory and typing:

```
sudo ./load
```

And then going into Administration > Networking and "Activating" the wireless connection. It doesn't work unless I do this every time I log in. This is really annoying, and I'd like to automate it so that it loads on startup.

In their Install document, Intel suggests that I create a new file /etc/modules.d/ipw3945 and insert the following lines into it:

```
echo install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; \
sleep 0.5 ; /sbin/ipw3945d --quiet >> /etc/modules.d/ipw3945

echo remove ipw3945  /sbin/ipw3945d --kill ; \
/sbin/modprobe -r --ignore-remove ipw3945 >> /etc/modules.d/ipw3945
```

When I test it, as suggested, with:

```
modprobe ipw3945
ps -C ipw3945d
```

The terminal comes up with:
```

PID TTY          TIME CMD
9683 ?        00:00:00 ipw3945d
```

The driver still wont load on startup, and I'm not sure what to do. Any ideas?

Thanks in advance.

---

### Post by ranf on 2006-04-08
[QUOTE=RiffX]
When I boot up, the wireless connection is not found at all. I can MANUALLY load the driver by navigating to the install directory and typing:

```
sudo ./load
```
[/QUOTE]
If that works, post its contents please.

[QUOTE=RiffX]
In their Install document, Intel suggests that I create a new file /etc/modules.d/ipw3945 and insert the following lines into it:

```
echo install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; \
sleep 0.5 ; /sbin/ipw3945d --quiet >> /etc/modules.d/ipw3945

echo remove ipw3945  /sbin/ipw3945d --kill ; \
/sbin/modprobe -r --ignore-remove ipw3945 >> /etc/modules.d/ipw3945
```
[/QUOTE]
To me it looks like this is a shell script that creates the /etc/modules.d/ipw3945 file.
But I don't have this directory. /etc/modutils/ looks like it could be what you need.
Let's have a look at the `load' script first.

---

### Post by RiffX on 2006-04-08
Hi, thanks for helping me.

The ./load script is as follows:

```
#!/bin/sh
# Copyright (C) 2004-2005 Intel Corporation
MODULE=ipw3945

function check_root()
{
	[ `whoami` != "root" ] &&
		echo "You must be root to run this script." &&
		return 1
}

function unload()
{ 
	./unload -ipw3945d=${path} || return 1
}

function load_pre
{
    for i in firmware_class; do
	if ! (lsmod | grep -q $i) && \
	    ! (modprobe $i > /dev/null 2>&1 && LOADED="${LOADED}${i} ") && \
	    ! (grep -q request_firmware /proc/kallsyms); then
	    if [ ! -e /proc/kallsyms ]; then
		echo "Could not be determine if firmware_class is already loaded."
		echo "Attempting to load driver anyway..."
	    else
		echo "Firmware capabilities not found.  See INSTALL."
		return 1
	    fi
	fi
    done
}


function load_modules
{
    I_DEBUG=""
    
    for i in ieee80211; do
	modprobe ieee80211 ${I_DEBUG} && LOADED="${LOADED}${i} "
    done
    
    insmod ./${MODULE}.ko $@ && LOADED="${LOADED}${MODULE} "
}

function load()
{
	load_pre && load_modules $@ && {
		if [ -z "${LOADED}" ]; then
			echo "No modules loaded."
		else
			echo "Loaded: ${LOADED}"
		fi

		return 0
	} 

	echo "Load failed."

	return 1
}

function parse_args()
{
        driver_args=
        while [ "$1" ]; do
                case $1 in
                -ipw3945d=*)
                        path=$1
                        path=${path/*=//}
                        shift
                        ;;
		
		--)
			shift
			break
			;;

		*)
			driver_args="$driver_args $1"
			shift
			;;
		esac
	done

	daemon_args=$@
	path=${path/%\//}/
	
	[ -x ${path}ipw3945d ] || {
cat << EOD
${path}ipw3945d does not exist or is not an executable.

You can specify the path for the ipw3945d via the -ipw3945d parameter:

	% ./load -ipw3945d=~/bin

The above will attempt to locate ipw3945d in the ~/bin directory.
EOD
		return 1
	}

}

unset LOADED

path=/sbin

parse_args $@ &&
unload && 
load $driver_args && 
echo -n "Loading ipw3945d."
${path}ipw3945d $daemon_args && 
echo -n "." &&
sleep 1 &&
echo -n "." &&
sleep 1 &&
echo "done."

```

---

### Post by ranf on 2006-04-08
Simply speaking it loads a kernel module `ipw3945'
and then runs a daemon(?) named `ipw3945d'.

For a module you always want to have loaded you simply put its name into /etc/modules

But I'm not so sure what a good place for starting the daemon is.

Anybody else?

---

### Post by RiffX on 2006-04-08
Hmmm... It's interesting you should mention daemon loading, because Intel's install guide contains the following passage:

```
3.  AUTOMATIC DAEMON LOADING VIA MODPROBE
-----------------------------------------------

There are some typical steps that are fairly generic in order 
to automate the launching of the daemon you can use your 
distribution's modprobe configuration.  To do this, you need to copy 
ipw3945.ko into your depmod path.  This is typically done via:

	# cp ipw3945.ko /lib/modules/$(uname -r)
	# depmod -a

Now, when you run modprobe it will load the module (and any dependencies, 
such as ieee80211.ko) and modprobe -r will remove the module.  The next 
step is to automate the launching and unloading of the regulatory 
daemon.  To do this, you typically place the following two lines into 
your /etc/modprobe.conf or into a new file /etc/modules.d/ipw3945:

	# echo install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; \
sleep 0.5 ; /sbin/ipw3945d --quiet >> /etc/modules.d/ipw3945

	# echo remove ipw3945  /sbin/ipw3945d --kill ; \
/sbin/modprobe -r --ignore-remove ipw3945 >> /etc/modules.d/ipw3945

NOTE:  The \ above is to continue the entered line to the next line (the 
lines added to the file are wider than 80 columns and so would wrap)

On some distributions you then may need to run the 'modules-update' 
script.

To verify if the above is working, you can type:

	# modprobe ipw3945
	# ps -C ipw3945d

If you see a running 'ipw3945d' then it launched the daemon for you.
```

I've tried setting this up, and adding the word 'ipw3945' to the end of /etc/modules, but it still doesn't seem to load it.

Anybody have any ideas?

---

### Post by tassoman on 2006-04-09
Should be just needed to run ./load in startup, as last action of bootstrap?

---

### Post by RiffX on 2006-04-09
Um... Could someone tell me how to do this...? I'm a bit of a newb...! ;-)

---

### Post by List on 2006-05-11
[QUOTE=RiffX]Um... Could someone tell me how to do this...? I'm a bit of a newb...! ;-)[/QUOTE]

Dir for the ipw3945-file should be /etc/modprobe.d/ **not** /etc/modules.d/

hope this helps ;)

---

