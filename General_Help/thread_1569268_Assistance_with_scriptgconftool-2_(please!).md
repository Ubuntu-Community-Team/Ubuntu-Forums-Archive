---
title: "Assistance with script/gconftool-2 (please!)"
date: 2010-09-06
forum: General Help
---

### Post by Forgotten Path on 2010-09-06
I have recently gotten in to writing my own scripts, and I have recently challenged myself to write a script that would automatically connect my computer to the internet through my cell phone whenever the phone is connected to the computer.  Here is what I have so far:

/etc/udev/rules.d/android.rules
```
# This rules file is for Android OS based mobile devices, by manufacturer.
# HTC
SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666", GROUP="plugdev", OWNER="brent", RUN+="/home/brent/bin/udev_netdroid.sh"
```

/home/brent/bin/udev_netdroid.sh
```
#!/bin/bash
#
# This script is meant to be called by an udev rule created for celluar phones with the Android OS (and Proxoid installed)
#
# When an Android phone is connected: 
# Starts the Android Debug Bridge server, begins port forwarding to Android phone (port 8080), and sets Gnome proxy settings.
#
# and
#
# When an Android phone is disconnected:
# Kills the Android Debug Bridge server, and returns Gnome proxy setting to normal.


# The important stuff
case $ACTION in
	add )
		sleep 5
		# Start Android Debug Bridge server
		/home/brent/bin/adb start-server
		/home/brent/bin/adb devices > /home/brent/log.txt
		# Start port forwarding to Android phone (port 8080)
		/home/brent/bin/adb forward tcp:8080 tcp:8080
		echo "ADB forwarding  $?" >> /home/brent/log.txt
		# Activate Gnome proxy
		/usr/bin/gconftool-2 -t string -s /system/proxy/mode "manual"
		echo "Activate Gnome proxy  $?" >> /home/brent/log.txt
		/usr/bin/gconftool-2 -t bool -s /system/http_proxy/use_http_proxy true
		echo "Use proxy  $?" >> /home/brent/log.txt
		# Gnome proxy http settings
		/usr/bin/gconftool-2 -t string -s /system/http_proxy/host "localhost"
		echo "HTTP host setting  $?" >> /home/brent/log.txt
		/usr/bin/gconftool-2 -t int -s /system/http_proxy/port "8080"
		echo "HTTP port setting  $?" >> /home/brent/log.txt
		# Gnome proxy https settings
		/usr/bin/gconftool-2 -t string -s /system/proxy/secure_host "localhost"
		echo "HTTPS host setting  $?" >> /home/brent/log.txt
		/usr/bin/gconftool-2 -t int -s /system/proxy/secure_port "8080"
		echo "HTTPS port setting  $?" >> /home/brent/log.txt
	;;
	remove ) 
		echo "success" >> /home/brent/remove.txt
		# Stop Android Debug Bridge server
		/home/brent/bin/adb kill-server
		# Disable Gnome system proxy
		/usr/bin/gconftool-2 -t string -s /system/proxy/mode "none"
		/usr/bin/gconftool-2 -t bool -s /system/http_proxy/use_http_proxy false
	;;
	* ) 
		echo $ACTION >> /home/brent/action.txt
esac

# Goodbye
exit 0
```

(The echo commands provide me a simple log file in my home folder)

When I plug in my phone, udev correctly identifies it, and runs the script.  When the script runs, it successfully starts the ADB server and begins port forwarding on the phone.  However, all my proxy settings do not change, despite the

```
echo " blah blah $?" >> ~/log.txt
```

commands outputting zeros for every command in my log file.  I have the feeling that since the gconftool-2 commands are being ran as root that it is only changing the root user's settings.  (Or am I using the "?" system variable incorrectly?)  Is there any way to use sudo or a similar command to run the commands as the currently logged on user?  And does anyone know how to apply the system proxy settings system wide from the command line?

The second major issue is the script doing absolutely nothing when the phone is removed.  Is the $ACTION variable set as something other than remove?  If so, why is it not outputted to ~/action.txt?

Thanks for any feedback!

---

### Post by Forgotten Path on 2010-09-06
I just spotted a mistake and changed the beginning of udev_netdroid.sh from


```
# The important stuff
case $ACTION in
	add )
		sleep 5
		# Start Android Debug Bridge server
		/home/brent/bin/adb start-server
```

to

```
# The important stuff
sleep 5
case $ACTION in
	add )
		# Start Android Debug Bridge server
		/home/brent/bin/adb start-server
```

The sleep command is needed to give the system time to recognize the phone is connected before the ADB commands are ran.  Also adding in some logging for the second half of the script.

---

### Post by Forgotten Path on 2010-09-07
Does no one have any ideas??  I'm really banging my head against the wall with this one.

I've tried:

```
sudo -u brent gconftool-2 -t string -s /system/proxy/mode "manual"
```

And I still get a 0 for the $? variable...  But none of the settings change whatsoever.  Any ideas?

---

### Post by Forgotten Path on 2010-09-07
Well, I seem to be getting absolutely no replies.  :(

Any moderator out there who thinks I may get more replies in "Desktop Environments", go ahead and move the thread...  And sorry for using up your time with that request...

---

