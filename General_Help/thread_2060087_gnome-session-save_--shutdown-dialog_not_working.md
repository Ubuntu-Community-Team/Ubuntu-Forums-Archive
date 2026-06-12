---
title: "gnome-session-save --shutdown-dialog not working"
date: 2012-09-19
forum: General Help
---

### Post by LuniTux on 2012-09-19
Hello,

I have a cron script that shuts down the computer after running a backup script. The script can not be run as root. Until recently, the script worked fine. However, the past few days the computer was still on in the morning. I tried to run the script manually but I am getting the following error:

**** (gnome-session-save:1601): WARNING **: Failed to call shutdown: The name org.gnome.SessionManager was not provided by any .service files**

Here is my cron script:

```
29 10 * * * env DISPLAY=:0 /home/lunitux/.backup/backup.sh
```

and here is my ~/backup/backup.sh file:

```
#! /bin/bash

#shutdown the virtual server
VBoxManage controlvm "MyServer" acpipowerbutton

#sleep until virtual server is completely shutdown
while [ "`VBoxManage showvminfo MyServer | grep running | tr -s " " | cut -d" " -f2`" == "running" ]; do
    sleep 1
done

#erase backups older than 5 days
cd /mnt/backup/
for filename in `ls | grep vdi | cut -d"." -f1`; do
	if [ $((`date +"%s"` - `date -d"$filename" +"%s"`)) -gt 432000 ]; then    #Older than 5 days
		rm -rf $filename.vdi;
	fi
done

#copy server image as a datestamped file to backup location
cp ~/.VirtualBox/HardDisks/server.vdi /mnt/backup/`date +"%Y%m%d"`.vdi

#shutdown the host computer. 
#This is the line that is not working...
gnome-session-save --shutdown-dialog
#

```

---

### Post by LuniTux on 2012-09-20
Hello me,

I have found an altenative but **NOT** a solution. If I replace:

```
gnome-session-save --shutdown-dialog
```

with

```
dbus-send --print-reply --system --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```

The script can now shut down the computer properly.

I don't know if there is any side effect by using this command though...

---

