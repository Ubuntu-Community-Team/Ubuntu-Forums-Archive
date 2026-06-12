---
title: "Crontab won't execute gconftool-2 commands in a script"
date: 2009-11-22
forum: General Help
---

### Post by Derek S on 2009-11-22
I'm trying to use a script to randomly change my gnome background on Ubuntu 9.10 Karmic.  My script is .ChangeWallpaper.sh and is executable

                                 ```
#!/bin/bash 
# Script to randomly set Background from files in a directory 
# Directory Containing Pictures 
DIR="/home/me/Pictures/InterFaceLift" 
# Command to Select a random jpg file from directory 
PIC=$(ls $DIR/*.jpg | shuf -n1) 
# Command to set Background Image 
# gconftool -t string -s /desktop/gnome/background/picture_filename $PIC 
# or
/usr/bin/gconftool-2 --set /desktop/gnome/background/picture_filename --type string $PIC
# Dump result to file for troubleshooting
echo $PIC >> /home/me/debug
```This script works perfectly from the command line.  When ran by crontab it executes and puts a random jpg filename into the debug file.  So I know all the variables and commands work.  It just doesn't run the gconftool-2 command, or the gconftool command when it is uncommented.
My crontab -e is ```
# m h dom mon dow command
*/10 * * * * /home/me/.ChangeWallpaper.sh
```Now after some searching I found a workaround but it seems very messy and should be unnecessary.  Apparently the following is required since Ubuntu Intrepid

Create a script called Make_Xdbus make it executable                                   ```
#!/bin/bash 
# Export the dbus session address on startup so it can be used by cron 
touch $HOME/.Xdbus 
chmod 600 $HOME/.Xdbus 
env | grep DBUS_SESSION_BUS_ADDRESS > $HOME/.Xdbus 
echo 'export DBUS_SESSION_BUS_ADDRESS' >> $HOME/.Xdbus 
# Export XAUTHORITY value on startup so it can be used by cron 
env | grep XAUTHORITY >> $HOME/.Xdbus 
echo 'export XAUTHORITY' >> $HOME/.Xdbus
```Add this script to your startup applications and / or run it to create .Xdbus
Create a Crontab job to run .Xdbus to set variables and then execute the wallpaper script
                                  ```
*/10 * * * * . /home/me/.Xdbus; /home/me/.RandomWallpaper.sh
```My questions are:  

Is there an easier way to make my script work with crontab?
Is this a bug in crontab?  If so how can I submit a bug report to the developers

---

### Post by PiniouF on 2010-01-14
Same problem since I installed Karmic... :(
Any idea ?

---

### Post by rapidwiz on 2010-01-20
Try this, it is similar to the above response

#!/bin/bash 

# This function required in order to run gconftool-2 from cron
# ================================================== ====
function export_variables
{
user=$( whoami )
pid=$( pgrep -u $user gnome-panel )

for dbusenv in $pid; do
DBUS_SESSION_BUS_ADDRESS=$( grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//' )

data="DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS"
eval " export $data"
done
}
# ================================================== ====
export_variables
# =====
####################################################################


ImageDir="/Public/Wallpaper/webilder/Collection/"


COUNT=`find $ImageDir | grep -v .thumbs | grep .jpg  | wc -l`

# --> Create Random Number
((NUM=RANDOM%COUNT))

# Find Image and grep for .jpg twice, one for all .jpg's, second to print line number on .jpg's and grep for the line num
IMG=`find $ImageDir | grep -v .thumbs | grep -v thumb | grep .jpg | grep -n .jpg | grep "^$NUM:" | awk -F ":" {'print $2'}`

echo "$IMG"

/usr/bin/gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$IMG"

/usr/bin/gconftool-2 -t str -set /desktop/gnome/background/picture_options "scaled"

---

### Post by beameup on 2010-01-31
Any reason you won't just use Webilder?

[http://www.webilder.org/download.html]("http://www.webilder.org/download.html")

Latest 0.6.5 is working for web downloads, but so far only the manual install.

You can create your own folder and drop it in the hidden .webilder folder in your home directory, and it will use those too.

---

### Post by zzart on 2010-05-17
the .Xbus didn't work for me (ubuntu 9.10 ) but i ve modified your script and added dbus using geirha's code ([http://ubuntuforums.org/showthread.php?t=1147321](http://ubuntuforums.org/showthread.php?t=1147321))

this script looks like this now and it workes with cron

> 
#!/bin/bash

# Get the pid of nautilus
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)

# If nautilus isn't running, just exit silently
if [ -z "$nautilus_pid" ]; then
  exit 0
fi

# Grab the DBUS_SESSION_BUS_ADDRESS variable from nautilus's environment
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')

# Check that we actually found it
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
  echo "Failed to find bus address" >&2
  exit 1
fi

# export it so that child processes will inherit it
export DBUS_SESSION_BUS_ADDRESS

#script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/path/to/dir"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC
date >> /tmp/test.txt



---

### Post by xile_ on 2011-03-11
@zzart - tried and tested in Gnome 2.32.0 and Ubuntu 10.10 and works like a charm.

Thanks!

---

### Post by r.osmanov on 2011-03-11
Had the same problem. [This]("http://ubuntuforums.org/showpost.php?p=7210276&postcount=8") helped.

---

### Post by dcstar on 2011-03-12
> **Derek S said:**
> I'm trying to use a script to randomly change my gnome background on Ubuntu 9.10 Karmic.  My script is .ChangeWallpaper.sh and is executable
.........
My questions are:  

Is there an easier way to make my script work with crontab?
Is this a bug in crontab?  If so how can I submit a bug report to the developers

The is **nothing** wrong with crontab. Cron jobs know **nothing** about what X session **you** want to output any GUI commands to - you must specifically set the X Display environment variable in the command string.

The simplest thing to do is to run the script inside your Gnome login session by adding it to System-Preferences-Startup Applications with code like the following:

```

DELAY=5m
PREFIX=~/
OUTPUT=.xplanet.png
#Code that creates "$PREFIX$OUTPUT" file for Xplanet backgrounds removed
.......
# Update Gnome backgound - this works in Ubuntu 9.04 & 10.04
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
rm $lockfile
exec $0
```

---

### Post by hcaicedo on 2011-07-22
The solution in #7 worked for me. Thanks

---

### Post by perspectoff on 2011-07-22
As an aside, cron events requiring root user privileges are added:

 sudo crontab -e

---

