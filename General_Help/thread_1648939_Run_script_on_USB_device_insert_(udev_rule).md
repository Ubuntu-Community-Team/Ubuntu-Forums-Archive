---
title: "Run script on USB device insert (udev rule)"
date: 2010-12-19
forum: General Help
---

### Post by Grenage on 2010-12-19
Greetings!

I have a udev rule, which runs a script when a drive is inserted:

```
ACTION=="add", ATTRS{idVendor}=="0951", ATTRS{idProduct}=="1607", RUN+="/home/grenage/auto_import.sh"
```

The script runs, but the bulk of the code doesn't.  It references the USB mount point (/media/Jabberwocky), and that path doesn't seem to exist yet; I'm assuming that udev runs the script *and then* mounts the drive.

```
if [[ -d /media/Jabberwocky ]]
then
    bla bla bla
fi
```

Does anyone have any suggestions?

---

### Post by Grenage on 2010-12-20
I had to hack my way around it.  I referenced a basic script in udev, which runs another script and exits; the exit is important, because the udev rule will otherwise wait for script one and two two finish before mounting.  I also added a *sleep 5* to the second script:

udev rule:
```
ACTION=="add", ATTRS{idVendor}=="0951", ATTRS{idProduct}=="1607", RUN+="/home/grenage/scripts/auto_import_relay.sh"
```

script one (auto_import_relay.sh):
```
#!bin/bash
/home/grenage/scripts/auto_mount.sh & exit
```

Script two (auto_import.sh):
```
#!bin/bash
sleep 5
*random code*
```

---

### Post by cedardoc on 2011-03-11
Hi, I searched in vain for this a while ago, and then stumbled across the fact that the application RealtimeSync can be setup to run any command you'd normally run at a terminal.

For example, I have a bash script that dismounts my phone's sd card:

#!/bin/bash  
pkill RealtimeSync 
# stops other folder watching activity
eject /media/BBSDCARD
eject /media/BLACKBERRY1
RealtimeSync /home/david/watch4bbsdcard.ffs_real

and when that RealtimeSync instance runs when I plug in the phone again it does this as a terminal command:

"/home/david/Desktop/startRealSyncs.py"

Then in that python script I have this:

#!/usr/bin/python 
import subprocess
import os
os.system("bash '/home/david/killRealtimeSync.sh'")
#that stops the usb connection watching

subprocess.call(['xdg-open', '/home/david/Main.ffs_real']) 
#that starts up a different folder I'm watching for changes (to sync between desktop and phone)


this isn't so much for the initial poster, but more for others that are newer to linux like me.

---

### Post by wardy277 on 2011-04-06
I have been mucking around with udev for a few days now, experimenting with things here and there. my main goes was to be able to plug in my cameras SD card into a USB card reader, and get it automatically backed up to a drive.

I was getting quite frustrated with it until i found this post. The simple fix of running a script to call another worked flawlessly. Before it seemed to run my script after the card was removed. i have added my code in case anyone else is interested. (I am also doing it in case my pc dies i have a backup of how i did it here ;))

I have also got it using the notify-OSD to let me know when it is done. Needs installing following package:
```
sudo apt-get install libnotify-bin
```


Hack to get libnotify to actually do anything as its run as root. add the following to /usr/local/bin/alt-notify-send
```
#!/bin/sh
user=`whoami`
pids=`pgrep -u $user gnome-panel`
title=$1
text=$2
timeout=$3
icon=$4

if [ -z "$title" ]; then
 echo You need to give me a title >&2
 exit 1
fi
if [ -z "$text" ]; then
 text=$title
fi
if [ -z "$timeout" ]; then
 timeout=60000
fi

for pid in $pids; do
 # find DBUS session bus for this session
 DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
 /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
 # use it

 #icon hack:
 if [ -z $icon ]; then
 DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
 notify-send -u low -t $timeout "$title" "$text"
 else
 DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
 notify-send -u low -t $timeout -i "$icon" "$title" "$text"
 fi
done

```

Finding unique codes (my device is sdc1):
```
udevadm info -a -p $(udevadm info -q path -n /dev/sdc1) | grep idVendor | head -1
```
```
udevadm info -a -p $(udevadm info -q path -n /dev/sdc1) | grep idProduct | head -1
```

add a new file at /etc/udev/rules.d/91-sync.rules and fill with the following, replacing the idVendor and idProduct with the values retrieved above, (i am not sure if the symlink is needed)
```
KERNEL=="sd?1", BUS="usb", SYSFS{idVendor}="05e3", SYSFS{product}="0723", NAME="usb/%k", SYMLINK="photos"
RUN+="/home/user/scripts/sync_photos_relay.sh"
```

my 2 scripts:
sync_photos_relay.sh
```
#!bin/bash
/home/user/scripts/sync_photos.sh & exit
```

sync_photos.sh
Remember to replace the user and group with your details. The chown is needed as the new files are created as root so u cant even see them.
The last line is the notifyOSD line, u can use any image you want, or just delete the path to the image to not show one.
I did a quick check if destination exists and if a file exists on the source just as a failsafe to make sure its the correct card. I think the idVendor and idProduct are for the USB card reader not the card
```
#!bin/bash
sleep 2


if [ -f /media/EOS_DIGITAL/sync -a -d /media/photos/DCIM/ ] 
then	
	rsync -ru /media/EOS_DIGITAL/DCIM/ /media/photos/DCIM/
	chown -R USER.GROUP /media/photos/DCIM/
	su USER alt-notify-send "Photos Sync" "Syncronization complete" 1000 "/home/user/scripts/synchronize.png"
fi

```

credits to the original poster and [http://blog.mirsal.ennaime.org/how-to-write-udev-rules]("http://blog.mirsal.ennaime.org/how-to-write-udev-rules")

---

