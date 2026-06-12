---
title: "Run command at boot time"
date: 2006-05-23
forum: General Help
---

### Post by jdavis on 2006-05-23
Hello,

I have a command that I would like to run when Ubuntu starts, this command requires sudo permissions.

When I run the command manually by using "sudo peerguardian start" then typing in my root password everything works ok, but i cannot seem to find a way to force this to start at startup. If possible i would like this to run without me having to type the root password.

This script also downloads some files to the location it is run in, so i have created a script that cd's to /tmp and then runs the process, which I have placed in bin, this saves my home dir from filling up with the files the process downloads:

```

#!/bin/bash
# start peerguardian
echo "Starting Peerguardian"
cd /tmp
sudo peerguardian start

```

but can anyone figure out a way i can run these commands automatically without any intervention from myself?

thanks, Jonathan

---

### Post by mscman on 2006-05-23
You're almost there!  All you need to do now is go to System > Preferences > Sessions and click on Startup Programs.  Click 'Add' and enter the name of the script.  It should do the work from there!

---

### Post by Slim Odds on 2006-05-23
[QUOTE=mscman]You're almost there!  All you need to do now is go to System > Preferences > Sessions and click on Startup Programs.  Click 'Add' and enter the name of the script.  It should do the work from there![/QUOTE]


You can also put stuff like this in rc.local

---

### Post by Jose Catre-Vandis on 2006-05-27
So this script won't require a password from the user if placed in Startup Programs?

Is the "sudo" required in the command?

---

### Post by Slim Odds on 2006-05-27
[quote=Jose Catre-Vandis]So this script won't require a password from the user if placed in Startup Programs?

Is the "sudo" required in the command?[/quote] 
the startup scripts run at root, so you can to anything you want (be careful)

to edit the startup scripts, you'll have to sudo some editor.

---

### Post by Jose Catre-Vandis on 2006-05-28
Not that I don't doubt you, but when using a sudo command in a script to get my wireless usb adapter up, as above, it does not work? Here is the script, which is loaded up in System>Preferences>Sessions>StartupPrograms. The script is executable by everyone, and owned by me as user on an auto login (It didn't work when owned by root either) The script works OK, as long as I enter the password for the first sudo command. If it was my PC I wouldn't worry, but have just converted the wife from XP! Where am I going wrong?

Here it is:
> #!/bin/sh

sudo modprobe prism2_usb prism2_doreset=1
sleep 2
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sleep 2
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem
sleep 2
sudo dhclient wlan0

---

### Post by Slim Odds on 2006-05-28
there is a file called /etc/init.d/rc.local

it is run last (after all of the other startup scripts)

it's runs as root

---

### Post by Jose Catre-Vandis on 2006-05-29
OK Slim

You will have to help me here, I am having a "thick" day!

I had a look at rc.local, and can see that its job is to run the local boot scripts. I shall therefore assume that it will run my script, as root, yes? Assuming it does, either with or without the sudo commands, I am not getting my wlan0 up when booting has finished. I then have to run the script manually and enter the sudo password to get wlan0 connected. Lost and confused? I know it should be easier than this :-) Thanks for your time and trouble.

---

### Post by AMTravesser on 2008-04-04
in /etc/crontab:

@reboot  root  <command>

to run as a regular user, replace root with the username.

---

