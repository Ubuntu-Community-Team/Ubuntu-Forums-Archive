---
title: "Regulating pwm fan speed (fancontrol) with hddtemp"
date: 2012-03-09
forum: General Help
---

### Post by s5narl on 2012-03-09
Hi everyone,

I'm trying to regulate the hard drive temperatures, as I live in the tropics, and the ubuntu server is located in an enclosed space with 6 hard drives, which can cause hard drive temperatures to rise to alarming levels (60 C!).

I've managed to install lm-sensors, hddtemp, and pwmconfig.  My system is a Biostar TA75A+, using an AMD A3850 chip.  There is only one pwm 4pin fan header on this motherboard (the CPU fan), and I'm using this header to control 1 CPU fan, and 4 chasis fans, using a pwm splitter cable and powered from the main power supply.  There are 6 Hitachi 7200rpm hard drives running off the Biostar TA75A+ motherboard.

So far, pwmconfig has successfully managed to configure and control all of the fans using the CPU temperature, but I need this to also read and respond to overheating on the hard drives.

Research on this has turned up what looks like a good script, but as I'm really very much a noob to scripting and ubuntu server, so I haven't been able to understand the scripting  and I can't understand how to modify/place the scripts properly.

[http://www.mentby.com/Group/lm-sensors/fan-control-based-on-hard-drive-temperatures.html](http://www.mentby.com/Group/lm-sensors/fan-control-based-on-hard-drive-temperatures.html)

Can anyone explain the script on the link, and how to install/adapt it?  Thank you all in advance!

---

### Post by s5narl on 2012-03-19
For anyone interested, I've managed to get it working in a fashion.  For some odd reason, hddtemp stopped working as a daemon, so fancontrol would not start properly.  I therefore need to manually start hddtemp, and then fancontrol.  

So after every reboot, first start hddtemp:
```
hddtemp -d /dev/sd*
```Then start fancontrol:
```
sudo fancontrol start &
```  If anyone can suggest how to fix this, and get the everything autostarted, that would be great.

I'll show in the next post what I did.

---

### Post by s5narl on 2012-03-19
What I did was to take the "script" in the post dated                                       Sun, 04 Jul 2010 23:52:33 -0700, and break it up into smaller instructions.

So first install the necessary software
```
apt-get install bc hddtemp file fancontrol

```Then create a script called "pct-fancontrol-hddtemp" in the location /usr/local/bin/
```
sudo nano /usr/local/bin/pct-fancontrol-hddtemp

```Cut and paste the following into the script/nano window
```
#!/bin/bash -e

# Company:  PowerCraft Technology
# Author:   Copyright Jelle de Jong <jelledejong*******>
# Note:     Please send me an email if you enhanced the script
# Version:  0.0.4
# Date:     2010-07-04 / 2010-07-05

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
# MA 02110-1301, USA.

PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin/

LC_ALL=C

# set -x
# exec 2>>/var/log/pct-fancontrol-hddtemp.log
# date=$(date)

DISKS="/dev/sd[a-z]"

# located in /var/lib/ so it will be there for fancontrol during boot
LOCATION=/var/lib/pct-fancontrol-hddtemp
FILE_MAX="$LOCATION"/pct-fancontrol-hddtemp-maximum
FILE_AVG="$LOCATION"/pct-fancontrol-hddtemp-average

DEGUG=0

[[ -e $LOCATION ]] || mkdir "$LOCATION"

while true
    do
    temperature=0
    summation=0
    maximum=0
    average=0
    count=0
    for value in $(hddtemp -n $DISKS 2>/dev/null)
    do
        temperature="${value//[!0-9]}"
        ((summation+=$temperature))
        ((count+=1))
        if [ $temperature -gt $maximum ]; then
            maximum=$temperature
        fi
        if [ $DEGUG = 1 ]; then
            average=$(echo "scale=1; $summation / $count" | bc)
            echo $summation
            echo $maximum
            echo $average
            echo $count
            echo "-----"
        fi
    done
    average=$(echo "scale=1; $summation / $count" | bc)
    # fancontrol output format
    echo "($maximum * 1000)/1" | bc > "$FILE_MAX"
    echo "($average * 1000)/1" | bc > "$FILE_AVG"
    sleep 45
done

exit

```After the script is done, it needs to be made executable
```
chown root:root /usr/local/bin/pct-fancontrol-hddtemp
chmod 755 /usr/local/bin/pct-fancontrol-hddtemp

```You will also need to setup fancontrol, which there are quite a few threads on, so I won't go into detail.  However, after setting up fancontrol, you will need to edit the fancontrol script since it won't see or use the hard drive temperatures.
```
sudo nano /etc/fancontrol

```Here is an example of what it should look like after you've edited it.  You need to insert references to "/var/lib/pct-fancontrol-hddtemp/pct-fancontrol-hddtemp-maximum" into the sensor/fancontroller that you want to linked to the hard drive temperature.
```
INTERVAL=10
DEVPATH=hwmon2=devices/platform/it87.3712
DEVNAME=hwmon2=it8728
FCTEMPS=hwmon2/device/pwm3=/var/lib/pct-fancontrol-hddtemp/pct-fancontrol-hddtemp-maximum
FCFANS= hwmon2/device/pwm3=hwmon2/device/fan1_input
MINTEMP= hwmon2/device/pwm3=40
MAXTEMP= hwmon2/device/pwm3=50
MINSTART= hwmon2/device/pwm3=60
MINSTOP= hwmon2/device/pwm3=20
MINPWM= hwmon2/device/pwm3=0
MAXPWM= hwmon2/device/pwm3=255

```I think this is where we autostart the hard drive temperature monitoring script
```
sudo nano /etc/rc.local 

```Insert the following
```
 /usr/local/bin/pct-fancontrol-hddtemp
```

And then we can restart the computer.  However, as mentioned, the whole thing will not autostart, and I will need to manually invoke the command in post 2 above.  So if anyone has any ideas as to how to fix the hddtemp (or whatever I did wrongly) so that the fancontrol can start at boot, that would be much appreciated!

---

