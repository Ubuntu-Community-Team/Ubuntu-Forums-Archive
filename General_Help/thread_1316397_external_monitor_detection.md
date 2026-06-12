---
title: "external monitor detection"
date: 2009-11-05
forum: General Help
---

### Post by Xbehave on 2009-11-05
I currently have the following aliases to get my external montior up and working
```
alias dualmr="xrandr --output VGA-0 --mode 1024x768 --right-of LVDS"
alias dualml="xrandr --output VGA-0 --mode 1024x768 --left-of LVDS"
alias dualma="xrandr --output VGA-0 --auto --output LVDS --auto"

```
However whenever i plug it in/unplug it i need to run the relevant command (dualmr for plugin / dualma for unplug), is there a way to automate this?
In the absence of automating it how could i get it to work on monitor the closing/opening of my lid? and on login?

*obviously the computer cant detect if i need dualmr or dualml so i don't mind having to run dualml when i need it as long as i can get dualmr to run by default.

---

### Post by codemedic on 2009-11-09
I embarked on the same issue over the weekend.

Here is what I did.

Modify /etc/acpi/lid.sh and add a line before the CheckPolicy call like below.

```

/home/user/bin/dock.sh auto

if [ `CheckPolicy` = 0 ]; then exit; fi

```

You can modify dock.sh the way you want it. Here is mine.
```


#!/bin/sh

# log or any output goes into /tmp/dock.log
exec >> /tmp/dock.log
exec 2>&1

echo
echo `date` - $0 "$@"

# Check what xradnr says
xrandr -q

get_dev_conf() {
	case "$1" in
		HDMI-1)
			echo "--auto --right-of LVDS";
			;;
		HDMI-2)
			echo "--auto --right-of HDMI-1";
			;;
		VGA)
			echo "--auto --right-of LVDS";
			;;
		TV)
			echo "--auto --right-of LVDS";
			;;
	esac;
}

restart_proc() {
	proc_name="$1";
	proc_cmd="$2";
	start_anyways="$3";
	proc_pattern="[${proc_name:0:1}]${proc_name:1}";

	pids=$( ps x | grep "$proc_pattern" | cut -d' ' -f1 )
	for p in $pids; do
		[ "$proc_name" = $( basename $( readlink -f /proc/${p}/exe ) ) ] &&
			ok_pids="$ok_pids $p";
	done;

	if [ -n "$ok_pids" ]; then
		kill $ok_pids &>/dev/null; sleep 1; kill -9 $ok_pids &>/dev/null
		$proc_cmd;
	elif [ -n "$start_anyways" ]; then
		$proc_cmd;
	fi
}

if [ "$1" = "desktop" ]; then
	xrandr --output HDMI-1 --auto --right-of LVDS --output LVDS --off;
	echo `date` - xrandr --output HDMI-1 --auto --right-of LVDS --output LVDS --off;
elif [ "$1" = "laptop" ]; then
	xrandr --output LVDS --auto --output HDMI-1 --off;
	echo `date` - xrandr --output LVDS --auto --output HDMI-1 --off;
elif [ "$1" = "auto" ]; then
	connected_devices=$( xrandr -q | grep ' connected' | egrep -v 'LVDS|TV' | cut -d' ' -f1 )
	
	## none other than LVDS or TV connected ?
	[ -z "$connected_devices" ] && exit 0;

	if [ grep -q closed /proc/acpi/button/lid/*/state ]; then
		for dev in $connected_devices; do
			opts="$opts --output $dev $( get_dev_conf $dev )";
		done
		xrandr $opts --output LVDS --off;
		echo `date` - xrandr $opts --output LVDS --off;
	else
		## maybe later; we have the key anyways
		exit 0;
	fi
else
	exit 0;
fi

restart_proc synergyc /home/user/bin/synergy

exit 0



```

This in addition to setting up my monitors, it deals with synergy restarts as well.

But unfortunately when I close my lid, it says in log :mad:

```

Mon Nov 9 10:21:58 GMT 2009 - /home/user/bin/dock.sh auto
Can't open display 

```

---

### Post by codemedic on 2009-11-09
It looks like gnome-power-manager or some other power management policy that interferes with the X screen setup. The X screen seems to get turned off each time.?!

If you have a big monitor attached to your docking station, isn't it normal to close the laptop lid when you near it and docked?!

---

### Post by codemedic on 2009-11-09
One another thing that I noticed while I was experimenting was the gnome-panel's auto hide doesnt seem to respond to my synergy'd mouse movements, fully. When the cursor is moved with events from synergys, the hiden panel doesnt show-up when it hits the screen border. Where as if I move the cursor with laptop's touchpad, it works. At the same time, if I move the cursor away from the screen edge with synergy the panel seems to respond and hides the panel !?!

May be i should log a bug!

---

### Post by codemedic on 2009-11-25
Bump...!!
Any suggestions / ideas?!

---

### Post by Xbehave on 2009-11-25
sorry been busy so i havent had a chance to try it, i do appreciate the help and will let you no if i can adapt it to my needs as soon as i have time to try.

Thx for the help

hmm it looks like fedora has a completly different layout for acpi files, have you tried adding the line export DISPLAY=:0 at the start of your script

---

### Post by Xbehave on 2009-11-28
I ruined up your script to only do the bit that i wanted (i also added do nothing if the setup is the same so that i can switch the setup manually and not get overwritten when i close the screen) and it works fine
```
#!/bin/sh
# log or any output goes into /tmp/dock.log
exec >> /tmp/dock.log
exec 2>&1
connected_device=$( xrandr -q | grep ' connected' | grep -vE 'LVDS' | cut -d' ' -f1)

#don't do anything if there is no change
[ -f /tmp/connected_displays ] && . /tmp/connected_displays
[ "$connected_device" = "$old_connected_device" ] && exit 0
echo old_connected_device="$connected_device" > /tmp/connected_displays

## none other than LVDS or TV connected ?
[ -z "$connected_device" ] && xrandr --auto && exit 0;

case "$connected_device" in
        VGA-0)
                xrandr --output LVDS --mode 1280x800 --output VGA-0 --right-of LVDS --mode 1152x864
                ;;
        *)
                xrandr --output LVDS --mode 1280x800 --output "$connected_device" --right-of LVDS
                ;;
esac;

exit 0

```
I ran into problems because it was being run as root so i replaced the command as myself instead of root 
on fedora it is 
```
/bin/su user -c "/etc/acpi/actions/displays.sh" 
```
on ubuntu it would be something like 
```
sudo -U user /home/user/bin/dock.sh auto
```
is working but will only work for the 1st login

update:
this works but is a bit ugly as it breaks if you ever login as somebody else, i'm trying to generalise the script using who and display
```
for user in `who | grep -E " :[0-9]? " | cut -f 1 -d ' '`;do
        su $user /etc/acpi/actions/xrandr-script.sh;
done

```

update2:
i only have one output so i simplified my scripts
```
#!/bin/sh
#errors goto  /tmp/xrandr-script.errors
exec >> /tmp/xrandr-script.errors
exec 2>&1

connected_device=$( xrandr -q | grep ' connected' | grep -vE 'LVDS' | cut -d' ' -f1)

if [ "$connected_device" ]; then
        if [ "`grep closed /proc/acpi/button/lid/*/state`" ]; then
                xrandr --output LVDS --off --auto
        else
                xrandr --output LVDS --mode 1280x800 --output VGA-0 --right-of LVDS --mode 1152x864
        fi
else
        xrandr --auto
fi

exit 0
```
I seam to run into crtc errors when i plug into some devices
Also i will update this when i figure out howto detect what i'm pluged into

---

### Post by Xbehave on 2009-11-29
ok i don't get it, my laptop crashed and now the script only if called without going through su

---

