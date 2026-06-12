---
title: "Run script as root after user login"
date: 2010-11-02
forum: General Help
---

### Post by nrune on 2010-11-02
I hate my touchpad when my mouse is plugged in, and because of a bug in the alps touchpad that the system does not shut off the touchpad when I am typing. and syndaemon does not work either. So I found this script that I modified and it works like a champ when run as sudo from a command line, but I can not get it work from root crontab with the "@reboot" and it does not work with ```
sudo update-rc.d killtouchpad start 30 2 3 4 5 . stop 70 0 1 6 .
```

So I am stumped and need of help. 

here is the script. 
```
#!/bin/bash
#
# Toggle touchpad on and off
#
# Author: Heath Thompson
# Email:  Heath.Thompson@gmail.com
#
# For startup wait for desktop to load first.
sleep 7
while true
do
	if ps -A | grep gnome-panel > /dev/null; 
	then
		#echo 'X loaded'
		break; 
	else
		#echo 'X not loaded, waiting...'
		sleep 5
	fi
done
#
# Check to see if appletouch is running
# if lsmod | grep appletouch > /dev/null; 
# then
# 	echo " * Appletouch enabled"; 
# else
# 	echo " * Appletouch either not working or not installed"
# 	killall mouseSwitcher
# fi

while true
do
	# 'xinput list' will list all input devices x detects
	# I could reference my usb mouse by ID but I'm afraid that if I plug
	# another device in before my mouse, it might not have the same ID each
	# time.  So using the device name makes it relatively fail-safe.
	if xinput list 'PS/2+USB Mouse';
	then
		# Found my usb wireless mouse
		# Disable everything on the Touchpad and turn it off
		modprobe -r psmouse;
		# Ends all syndaemon capturing which may have been used to monitor the touchpad/keyboard activity
	else
		# My usb wireless mouse isn't present we need the touchpad
		# Reenable Touchpad and configure pad-clicks
		# RTCornerButton is the Right Top Corner on the touchpad
		# 	The value 3 maps it as the right click button
		# RBCornerButton is the Right Bottom Corner on the touchpad
		#	The value 2 maps it as the middle click button
		modprobe psmouse;
		# Forces break of touchpad functions while typing if the touchpad is enabled.
		# Adds a 3 second interval following keyboard use which helps to prevent the
		# mouse from jumping while typing & resting hands on restpad or the touchpad
	
	fi
	
	# wait 2 seconds and poll the mouse state again
	sleep 2
done

sleep 15
```

Any help apprecated!

---

### Post by matt_symes on 2010-11-02
Hi

Is it an environment issue? Root does not have your environment.

You could also redirect output to a file and see what errors are happening.

Kind regards

---

### Post by nrune on 2010-11-02
Okay I tried that and the text output file was empty.  Funny thing is that it works just fine from command line.  Any ideas?

---

### Post by matt_symes on 2010-11-02
Hi

Type (at a terminal)

sudo su
and enter your password

Run the script again.   

Type exit.

Does the script work then?

This would suggest something different between you env and roots env if not.

Post the whole line in cron that is running the line @REBOOT to run your script

When you say update.rc is not working, what do you mean? Is it not creating the sym links? Can you elaborate.

Where are you keeping the script. What is the path?

Kind regards

---

