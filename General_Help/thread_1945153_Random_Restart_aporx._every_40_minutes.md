---
title: "Random Restart aporx. every 40 minutes"
date: 2012-03-22
forum: General Help
---

### Post by theoreo25 on 2012-03-22
hey guys, don't know what the issue is, running 10.10. if i update my system properly it wont do this, but if i turn off my computer the fan winds up and it restarts. there is no issue after it restarts, except it will do this every 40 minutes. im pretty sure this computer did the same thing with windows installed on it, but i didn't have it installed very long and as soon is i installed Ubuntu on the comp it didn't do this. but after running Ubuntu for about 4 months the computer returned to its old habits. ive been just performing the updates to prevent this but that quick fix isn't working anymore and its kind of annoying. any advice on how to tackle this issue is much appreciated. thanks

---

### Post by imachavel on 2012-03-22
that would be a setting configuration and not a software or hardware issue. No software or hardware failure will make the pc restart, it will blue screen or shut down completely, but not restart, unless it's a memory error.

Man, let me google this really quickly. I've never heard of a software failure causing a pc to restart, I'm pretty sure you have it configured to restart somewhere, but let me google around a bit anyway. Hello please do me a favor, open a terminal:

ctrl+alt+t

type in crontab -l and please post the output, OR, go to the search button top left(I assume you are using the unity interface, and search for terminal, it should be in applications, and don't know that is located in the interface directory. Pressing the gear looking icon on the top right and going to start up applications doesn't seem to find terminal for me

Now what output do you get from crontab -l, let me google around some more and see what other results come up. Thanks for your patience!

---

### Post by imachavel on 2012-03-22
well there is some more stuff you can look at, so sorry I spouted off like that, let's try some other things from the terminal as well:

sudo apt-get install lm-sensors

sudo sensors

sensors-detect

my read out after installing lm-sensors said:

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

now try this:

sudo apt-get install update

if your processor is overheating, or the heat sink fan isn't spinning fast enough, could be your machine is restarting to compensate for an over heating issue. Some other commands that might help you diagnose things, let's try this:

uname -r

try this:

--cut here--
#!/bin/bash

     
 # Here you can set several defaults.

# The number of devices to create (max: 256)
NUMBER=32

# The owner and group of the devices
OUSER=root
OGROUP=root
# The mode of the devices
MODE=600

# This script doesn't need to be run if devfs is used
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
echo "You do not need to run this script as your system uses devfs."
exit;
fi
fi

i=0;

while [ $i -lt $NUMBER ] ; do
echo /dev/i2c-$i
mknod -m $MODE /dev/i2c-$i c 89 $i || exit
chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
i=$[$i + 1]
done
--cut here--

I don't remember what that script will do, for me it closed the terminal. But I believe it's supposed to help overcome the no sensors detected driver status, although don't ask me how, as an uninstalled driver shouldn't be overcome by a script, unless the driver is installed, and linux just doesn't recognize the driver because of a back end c script error(MAYBE, DON'T QUOTE ME!)

ok and finally go to home, then look for file system near the buttom left under computer(assuming you are using unity and not gnome)

now go to var/ then to log/

and ummmmmmmmmmmmmmmmmmmmmmmmmmmmm................................

wow lots of logs in there. Which ones should you upload as attachments. I'd upload all the syslog and kern.log files, if possible. I can't say these are arranged by date, so it will be difficult to know which ones are more recent logs. Now for example my kern.log.1 file inside says quite a few things inside(see attached), so there will be quite a few things but if there is something wrong especially recently it should stand out(btw you might need to tarball the file to make it possible to upload the file)

---

### Post by theoreo25 on 2012-03-22
thanks you, it will take me some time to make full sense of your entire post, im not that quick with processing this type of information but ill post again when i make some progress.

---

### Post by theoreo25 on 2012-03-23
im running gnome... sorry i should have specified in the first place.

---

