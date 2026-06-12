---
title: "Halevt and permissions, commands running but not correctly"
date: 2010-11-19
forum: General Help
---

### Post by brennydoogles on 2010-11-19
I recently decided to attempt to implement automatically disabling my laptop's touchpad when my external mouse is connected, and I am just about there. Unfortunately, what I suspect to be a permissions problem is stopping me from succeeding. Here's what I have done so far:
[LIST=1]
[*]Written a Script which will enable or disable the touchpad based upon cli argument (verified to work when called via terminal)
[*]Set up a rule for halevt which successfully launches an arbitrary command when the mouse is connected or disconnected (even successfully logging itself)
[*]Determined that the script is in fact being called upon device connection (by adding echo statements to the script which are working)
[/LIST]

When launching halevt, I have even tried running it as my user/group, and with a special config file, all to no avail. Any help would be greatly appreciated!

Also, here is my command to run halevt:
```
sudo halevt -u brendon -g brendon -c /home/brendon/.halevt.xml
```

My .halevt.xml file:
```

<?xml version="1.0" encoding="UTF-8"?>
<halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">
	<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023">
		<halevt:Insertion exec="/home/brendon/bin/toggleTouchpad off"/>
		<halevt:Removal exec="/home/brendon/bin/toggleTouchpad on"/>
	</halevt:Device>
</halevt:Configuration>
```

And the script being run:
```

# toggleTouchpad by Brendon Dugan
# Toggles a touchpad on or off depending on it's current state or CLI argument
#
# To configure, run the command 'xinput list' in terminal and identify your touch pad.
# Using the output of the above command, change the touchpadString variable to a substring
# of your touchpad's description that is unique to that device.
#
# To run, simply type 'toggleTouchpad' to toggle your touchpad on or off, or
# 'toggleTouchpad on' to explicitly turn your touchpad on, or
# 'toggleTouchpad off' to explicitly turn it off.
#
# Enjoy!
touchpadString="TouchPad"
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $6}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')

# Check for arguments on the command line
if test $# -eq 1
then
	# Change the argument to lowercase
	arg1=$(echo $1 | tr [:upper:] [:lower:])
	cliArg=1
else
	# There is no argument.
	cliArg=0
fi

if [ $cliArg -eq 1 ]
then
	# If there's an argument, check to see whether it is on, off, or junk
	if [ $arg1 = 'on' ]
	then
		# The argument was 'on', so turn the touchpad on 
		xinput --set-prop $touchpadID "Device Enabled" 1
		echo "ON"
	elif [ $arg1 = 'off' ]
	then
		# The argument was 'off', so turn the touchpad off 
		xinput --set-prop $touchpadID "Device Enabled" 0
		echo "OFF"
	else
		# The argument was junk, so do nothing 
		sleep 1
	fi
else
	# There was no argument, so just toggle the touchpad to the opposite
	# of the state it has now.
	if [ $touchpadEnabled -eq 1 ]
	then
		xinput --set-prop $touchpadID "Device Enabled" 0
	else
		xinput --set-prop $touchpadID "Device Enabled" 1
	fi
fi

```

---

### Post by brennydoogles on 2010-11-19
*Polite bump*

---

### Post by brennydoogles on 2010-11-20
Another polite bump.

---

### Post by brennydoogles on 2010-11-20
*Bump* -- Somehow this thread managed to make it all the way to page 12 in just a few hours... this is a busy forum!

---

### Post by brennydoogles on 2010-11-23
Solved [here]("http://ubuntuforums.org/showthread.php?t=1628329")!

---

