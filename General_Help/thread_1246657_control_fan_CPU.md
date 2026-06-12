---
title: "control fan CPU"
date: 2009-08-22
forum: General Help
---

### Post by davidtuti on 2009-08-22
Hi,

I would like to know if exists a command to can develop a little script to control fan RPM checking the cpu temperature.

Many thanks and sorry for my english!

---

### Post by Whiffle on 2009-08-22
Maybe.  That is something that is hardware dependent, so we'll need to know what kind of motherboard (model numbers are nice) you've got.

---

### Post by davidtuti on 2009-08-22
> **Whiffle said:**
> Maybe.  That is something that is hardware dependent, so we'll need to know what kind of motherboard (model numbers are nice) you've got.

Thanks. I have:

Base Board Information
        Manufacturer: ASUSTeK Computer INC.
        Product Name: P5K
        Version: Rev 1.xx

---

### Post by DeMus on 2009-08-22
> **davidtuti said:**
> Thanks. I have:

Base Board Information
        Manufacturer: ASUSTeK Computer INC.
        Product Name: P5K
        Version: Rev 1.xx

This motherboard works very well with the software available for Ubuntu. I have an explanation (not my own btw) how to install this but it is not easy to do. I managed to make things work both with Hardy and Jaunty, but as I said it is absolutely not easy. Also because the explanation is not always very clear.
If you like I can post it, like I have done before for others.

---

### Post by davidtuti on 2009-08-22
> **DeMus said:**
> This motherboard works very well with the software available for Ubuntu. I have an explanation (not my own btw) how to install this but it is not easy to do. I managed to make things work both with Hardy and Jaunty, but as I said it is absolutely not easy. Also because the explanation is not always very clear.
If you like I can post it, like I have done before for others.

Many thanks!
I have install lm_sensors and I see the RPM fan but I don't know how to relate it with cpu temperature to can increase or decrease the RPM fan with the temperature

Many thanks!

---

### Post by whitethorn on 2009-08-22
After installing lm-sensors, you now need to run the program fancontrol. To configure the different fan speeds and temps, you need to first run.

```
sudo pwmconfig
```

Then you'll have set up fancontrol to run on boot it will use your config file from pwmconfig.

---

### Post by DeMus on 2009-08-22
> **davidtuti said:**
> Many thanks!
I have install lm_sensors and I see the RPM fan but I don't know how to relate it with cpu temperature to can increase or decrease the RPM fan with the temperature

Many thanks!

Here it goes. The file is too big to add as attachment so I have to just copy the text here:

-------------------------------------------------
Howto Install and Configure lm-sensors
========================

1. Install lm-sensors using apt-get or the Synaptic GUI.

```
sudo apt-get install lm-sensors
```


2. Run the mkdev.sh script in the lm-sensors source. It is extracted below:

a. Copy the script file below to a text editor and save it to a file named mkdev.sh.

```
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
#end of file
```

b. Make the file executable:

```
chmod 755 mkdev.sh
```

c. Run mkdev.sh from the current directory

```
sudo ./mkdev.sh
```


3. Now run sensors-detect and answer YES to all YES/no questions. I generally use the ISA bus rather than the SMBus bus, your choice to this question!. At the end of the detection phase, a list of modules that needs to be loaded will displayed. You will need to write these down or print the list for the next steps.

```
sudo sensors-detect
```

Below is an example of results from sensors-detect:
#************************************************* *****************************
To make the sensors modules behave correctly, add these lines to
/etc/modules:

```
#----cut here----
# I2C adapter drivers
i2c-viapro
i2c-isa
# I2C chip drivers
eeprom
it87
#----cut here----
```

Then, run ```
sudo /etc/init.d/module-init-tools
```

To make the sensors modules behave correctly, add these lines to
/etc/modprobe.d/local and run update-modules:

```
#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here----
#************************************************* *******************************
```


4. In this example, we add the modules in reverse order (order is critical!) in "/etc/modules".

```
#************************************************* *********************** 
# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line. Comments begin with
# a "#", and everything on the line after them are ignored.

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp

#For lm-sensors, i2c modules
it87
i2c-viapro
i2c-isa

#end of file!
#************************************************* ****************
```


4. I found that there was no "/etc/modprobe.d/local" and that "alias char-major-89 i2c-dev" was already listed in "/etc/modprobe.d/aliases". So, nothing to do here.


5.Now load the modules manually using modprobe and update the dependencies.

```
sudo modprobe i2c-sensor
sudo modprobe i2c-viapro
sudo modprobe i2c-isa
sudo modprobe it87

sudo depmod -a <may not be needed!>
sudo update-modules <may not be needed!>
```


6. Now test the sensor output using the lm-sensors utility "sensors".

```
sensors
```

************************************************** *****************
it87-isa-0290
Adapter: ISA adapter
VCore 1: +1.57 V (min = +1.42 V, max = +1.57 V) ALARM
VCore 2: +2.66 V (min = +2.40 V, max = +2.61 V) ALARM
+3.3V: +6.59 V (min = +3.14 V, max = +3.46 V) ALARM
+5V: +5.11 V (min = +4.76 V, max = +5.24 V)
+12V: +11.78 V (min = +11.39 V, max = +12.61 V)
-12V: -19.14 V (min = -12.63 V, max = -11.41 V) ALARM
-5V: +0.77 V (min = -5.26 V, max = -4.77 V) ALARM
Stdby: +5.00 V (min = +4.76 V, max = +5.24 V)
VBat: +3.12 V
fan1: 3668 RPM (min = 0 RPM, div =                   
fan2: 0 RPM (min = 664 RPM, div =                    ALARM
fan3: 0 RPM (min = 2657 RPM, div = 2) ALARM
M/B Temp: +39°C (low = +15°C, high = +40°C) sensor = thermistor
CPU Temp: +36°C (low = +15°C, high = +45°C) sensor = thermistor
Temp3: +96°C (low = +15°C, high = +45°C) sensor = diode
************************************************** ********************

7. Reboot Ubuntu and the sensors should now be detected during the boot process properly!

8. Run pwmconfig
Code:
```
sudo pwmconfig
```
One by one, all fans will be tested for 'speedcontrol' (Pulse Width Modulation, actually). Follow the onscreen help. Pwmconfig will write a config file in /etc. I set the interval to 5 seconds, just to be safe, but 10 should be fine too. Let the script run until you see "Select fan output to configure, or other action:" (all default options are fine, you can basically enter you way through the script).

Now press 5 to look at the configuration file. Press 1 to edit settings. Select a temperature that matches your CPU temp (usually the same number as the fan number, but check and double check!). Go with the defaults until you see: "Enter the minimum PWM value (0-255)
at which the fan STARTS spinning (press t to test) (150):"
Here, press t.
Keep pressing enter until you hear (or better: see) the fan spinning up. Then, press y and enter.
Same for the next step, but the other way around. If you see the fan stops spinning, press y and enter.

Press 5 again to display the config file one more time, then press 4 to save and quit. Almost there!

My /etc/fancontrol config looks like this:
Code:
INTERVAL=5
FCTEMPS= 1-0290/pwm2=1-0290/temp2_input
FCFANS= 1-0290/pwm2=1-0290/fan2_input
MINTEMP= 1-0290/pwm2=43
MAXTEMP= 1-0290/pwm2=53
MINSTART= 1-0290/pwm2=120
MINSTOP= 1-0290/pwm2=105
this is an example!

Starting fancontrol 
The last step is to start up fancontrol. Enter this:
Code:
```
sudo fancontrol &
```
Now you can see and hear that your CPU fan is running slower, unless your CPU heats up. Good stuff!

[B}Starting fancontrol automatically on boot[/b]
Create a file called "fancontrol" in /etc/init.d:
Code:
```
sudo gedit /etc/init.d/fancontrol
```
And paste this in there:
```
Code:
#!/bin/sh
#
# Fancontrol start script.
#

set -e

# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol.pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


case "$1" in
        start)
                log_begin_msg "Starting fancontrol daemon..."
                start-stop-daemon --start -o -q -m -b -p $PIDFILE -x $DAEMON
                log_end_msg $?
                ;;
        stop)
                log_begin_msg "Stopping fancontrol daemon..."
                start-stop-daemon --stop -o -q -p $PIDFILE
                log_end_msg $?
                ;;
        force-reload|restart)
                sh $0 stop
                sh $0 start
                ;;
        *)
                log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload}"
                log_success_msg "  start - starts system-wide fancontrol service"
                log_success_msg "  stop  - stops system-wide fancontrol service"
                log_success_msg "  restart, force-reload - starts a new system-wide fancontrol service"
                exit 1
                ;;
esac

exit 0
```
Save and close, then run 

```
sudo update-rc.d fancontrol defaults 99 01
sudo cp /etc/rc5.d/fancontrol /etc/rc.local/fancontrol
sudo chmod +x /etc/rc.local/fancontrol
```
and you should be set.

(Thanks, Mr Wonka and jotape99!)
-------------------------------------------------

Good luck with it, but be careful what you are doing.

---

### Post by 3rdalbum on 2009-08-22
If you've got an Asus P5K motherboard, then just go into your BIOS and turn on Q-Fan for the CPU cooler. It will then run faster or slower depending on the CPU temperature, and your CPU will never overheat. The motherboard can control the CPU cooler better than you or I can.

---

### Post by Dansaycool on 2009-09-08
Hi,

I ran the pwmconfig a few times because I kept changing my mind on what speeds to run the fans at over the course of one day and now I'm running into a problem. The problem being I can't control the fans anymore.. there just running on full constantly. If I try to stop fancontrol it says it can't find the process and if I try to start it, no change in speeds seem to happen with the fans? Anyone ran into this before?

---

