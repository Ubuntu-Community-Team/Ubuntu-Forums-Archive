---
title: "lmsensors- where is it?"
date: 2011-09-13
forum: General Help
---

### Post by sumithar on 2011-09-13
I want to find my CPU temperature and read that I can use lmsensors for this purpose.

When I look at Synaptic I see the following packages are installed
lm-sensors
libsensors4
sensors-applet
libsensors-applet-plugin0

But I can't find it anywhere so I can click on it to execute the app.

Any suggestions?

Am using Ubuntu 11.04 with Unity interface.

Thanks!

---

### Post by 2F4U on 2011-09-14
Try

```
whereis sensors
```

to locate the package. If it is installed, you have to configure it before you can use it, so do

```
sudo sensors-detect
```

in a terminal and run through the questions.

---

### Post by sumithar on 2011-09-14
> **2F4U said:**
> Try

```
whereis sensors
```

to locate the package. If it is installed, you have to configure it before you can use it, so do

```
sudo sensors-detect
```

in a terminal and run through the questions.

Thanks.  I did that- letting all of them default except the last one to load modules which I said yes.  Then it said to
service module-init-tools start

I did this but got an error
service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.70" (uid=1000 pid=2649 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))


~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

But I had already run sensors-detect?

---

### Post by stinkeye on 2011-09-14
Run it again answering **yes** to all.
There is also an indicator-sysmonitor available from this ppa.
[**_[COLOR="DarkRed"]https://launchpad.net/~alexeftimie/+archive/ppa[/COLOR]_**]("https://launchpad.net/~alexeftimie/+archive/ppa")

---

### Post by vasa1 on 2011-09-14
> When I look at Synaptic I see the following packages are installed
lm-sensors
libsensors4
sensors-**applet**
libsensors-**applet**-plugin0
Isn't it correct that applets won't work in 11.04 and that we now have to use "indicators"?

---

### Post by Frogs Hair on 2011-09-14
You could look at this PPA . [http://www.webupd8.org/2011/04/indicator-sensors-displays-cpu.html](http://www.webupd8.org/2011/04/indicator-sensors-displays-cpu.html)

---

### Post by sumithar on 2011-09-14
> **stinkeye said:**
> Run it again answering **yes** to all.
There is also an indicator-sysmonitor available from this ppa.
[**_[COLOR="DarkRed"]https://launchpad.net/~alexeftimie/+archive/ppa[/COLOR]_**]("https://launchpad.net/~alexeftimie/+archive/ppa")

I tried by responding Yes to everything with the same result as before.  

So I added the sources for that PPA and used synaptic to install indicator-sensor.
I then searched on "indicator" in the application launch menu and found an entry for "System monitor indicator".  When I clicked on it I could see cpu % and memory percent on the bar at the top.
I right clicked on it and chose preferences where it allowed me to add just one additional sensor for my HDD which looked like this
/dev/sda - WDC WD800BB-22JHC0 - 34C hddtemp///dev/sda
and it now shows along with the CPU and mem the value of 34C.

Is that the same as the CPU temperature?  Doesn't seem likely...

---

### Post by grahammechanical on 2011-09-14
I have xsensors installed. It has a graphical user interface. I have just installed on 11.10 beta that I am testing. It works fine. The Ubuntu software Centre (in 11.10) now gives an option to install an icon into the launcher.

When ever I get curious about temperature I click on the icon and I get readings for CPU and motherboard temperature as well as fan speeds for CPU Chassis and Power Supply Fans. As well as motherboard voltages.

I also have it working in 11.04.

Regards.

---

### Post by pqwoerituytrueiwoq on 2011-09-14
> **sumithar said:**
> I tried by responding Yes to everything with the same result as before.  

So I added the sources for that PPA and used synaptic to install indicator-sensor.
I then searched on "indicator" in the application launch menu and found an entry for "System monitor indicator".  When I clicked on it I could see cpu % and memory percent on the bar at the top.
I right clicked on it and chose preferences where it allowed me to add just one additional sensor for my HDD which looked like this
/dev/sda - WDC WD800BB-22JHC0 - 34C hddtemp///dev/sda
and it now shows along with the CPU and mem the value of 34C.

Is that the same as the CPU temperature?  Doesn't seem likely...
```
sudo hddtemp /dev/sda
```that is the temperature of your hard drive

basic install commands
```
sudo apt-get install sensors-applet;sudo sensors-detect;sensors
```you can added the sensor applet to your panel

---

### Post by sumithar on 2011-09-14
> **grahammechanical said:**
> I have xsensors installed. It has a graphical user interface. I have just installed on 11.10 beta that I am testing. It works fine. The Ubuntu software Centre (in 11.10) now gives an option to install an icon into the launcher.

When ever I get curious about temperature I click on the icon and I get readings for CPU and motherboard temperature as well as fan speeds for CPU Chassis and Power Supply Fans. As well as motherboard voltages.

I also have it working in 11.04.

Regards.

I installed xsensors 0.70 too.  I can find it in the applications menu but when I click on it I just get an empty window.  actually when I first click on it is just like a little button on the top left corner of my screen but I can drag and resize it to form the empty window. 

I first installed it from a website (forget which) and then thru synaptic- but same results.

---

### Post by sumithar on 2011-09-14
> **pqwoerituytrueiwoq said:**
> ```
sudo hddtemp /dev/sda
```that is the temperature of your hard drive

basic install commands
```
sudo apt-get install sensors-applet;sudo sensors-detect;sensors
```you can added the sensor applet to your panel

I've followed these instructions half a dozen times now but always with same result
[CODE}sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.[/CODE}

I have run sensors-detect many times and replied Yes to every question.

---

### Post by sumithar on 2011-09-14
Btw, this is the summary it gives after running sensors-detect

```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0xa10
    Chip `ITE IT8712F Super IO Sensors' (confidence: 9)

Driver `max6650':
  * Bus `Radeon i2c bit bus GPIOPAD_MASK'
    Busdriver `UNKNOWN', I2C address 0x1b
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)
  * Bus `Radeon i2c bit bus GPIOPAD_MASK'
    Busdriver `UNKNOWN', I2C address 0x1f
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)
  * Bus `Radeon i2c bit bus GPIOPAD_MASK'
    Busdriver `UNKNOWN', I2C address 0x48
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)
  * Bus `Radeon i2c bit bus GPIOPAD_MASK'
    Busdriver `UNKNOWN', I2C address 0x4b
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)

Driver `sbs':
  * Bus `Radeon i2c bit bus GPIOPAD_MASK'
    Busdriver `UNKNOWN', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Warning: the required module sbs is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check http://www.lm-sensors.org/wiki/Devices for
driver availability.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
max6650
#----cut here----
```

Don't know if it helps you gurus to point out something wrong...

---

### Post by albert s on 2011-09-19
make sure you have them installed in synaptic,
then 

```
sudo sensors-detect
```

answer Yes to everything
then
 
```
sudo /etc/init.d/module-init-tools restart
```

that might actually give you a different message, simple put in whatever it corrects it to,

you might have to reboot after that.

then in a terminal


```
sensors
```

^^^ CODE courtesy of BrokeMahPC

although I dont have my HDD temp showing, but I can live with that.

---

### Post by blueridgedog on 2011-09-19
I see another mentioned the sudo required for the module install.

You may also want to take a look at conky for temp. display:

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

It is an amazing tool.

---

### Post by sumithar on 2011-09-21
> **albert s said:**
> make sure you have them installed in synaptic,
then 

```
sudo sensors-detect
```

answer Yes to everything
then
 
```
sudo /etc/init.d/module-init-tools restart
```

that might actually give you a different message, simple put in whatever it corrects it to,

you might have to reboot after that.

then in a terminal


```
sensors
```

^^^ CODE courtesy of BrokeMahPC

although I dont have my HDD temp showing, but I can live with that.

actually when I try that 
```
sudo /etc/init.d/module-init-tools restart
```
command it told me to use
```
sudo service module-init-tools start
```
instead.

I did that, rebooted and tried the command sensors again
```
:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

---

### Post by sumithar on 2011-09-21
> **blueridgedog said:**
> I see another mentioned the sudo required for the module install.

You may also want to take a look at conky for temp. display:

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

It is an amazing tool.

I downloaded this and extracted it.  Following the install instructions I cd'd to the src directory and ran sh ./configure.  I got a screenfull of stuff and finally
```

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for funopen... no
checking for X... no
configure: error: Can't locate your X11 installation

```

This seems more trouble than it's worth just to find my CPU temperature ;-)

---

### Post by Mark Phelps on 2011-09-22
I had a similar problem on my previous PC.  The sensors-detect would run, find the same sensors as you reported, and then not show anything.  The fix was to add a parameter to the kernel line in GRUB.  Once that was added, running sensors again got a whole LIST of sensor readings.  I'm not at my Linux box, so I don't have that parm.  I'll check later tonight and update this thread tomorrow.

---

### Post by blueridgedog on 2011-09-22
> **sumithar said:**
> 
This seems more trouble than it's worth just to find my CPU temperature ;-)

Why not just install from synatic?

---

### Post by dozycat on 2011-09-22
try this:
sudo modprobe coretemp

the temps must be around:
/sys/class/hwmon..........temp1_input
using conky you can control the temps of the cpu cores.

---

### Post by sumithar on 2011-09-24
> **blueridgedog said:**
> Why not just install from synatic?

Duh!  Sometimes one forgets the obvious- thanks, I've done that...But it doesn't show the temp tho...see attached.

It's a rather peculiar app- for beginners I couldn't find it in the applications menu, so ran it from command line.
And then it has this little window which I cannot resize or do anything with.

Maybe I need to wait for the other poster's grub option to see the temp.

Rgds

---

### Post by sumithar on 2011-09-24
> **dozycat said:**
> try this:
sudo modprobe coretemp

the temps must be around:
/sys/class/hwmon..........temp1_input
using conky you can control the temps of the cpu cores.

Running the modprobe doesn't do anything that I can see- should I?

There is nothing in that directory
```
/sys/class/hwmon$ ls -la
total 0
drwxr-xr-x  2 root root 0 2011-09-24 10:56 .
drwxr-xr-x 45 root root 0 2011-09-24 10:15 ..

```

---

### Post by dino99 on 2011-09-24
from your post #12, it seems that lm-sensors cant identify your hardware sensors, so you might report against it:

ubuntu-bug lm-sensors

note: some hardware dont have sensors, or sometimes they are blacklisted by default ubuntu config, look at yours into: /etc/modprobe.d/blacklist.conf

on my system i use psensor

---

### Post by nrundy on 2011-09-24
I feel like some kind of Temperature monitor should be installed and active by default in the System Monitor.

---

### Post by Mark Phelps on 2011-09-24
OK ... the kernel parm that might work is "acpi_enforce_resources=lax"

Add that to your Linux kernel parms in /etc/default/grub

Reboot and then see if sensors picks up more readings.

This happens because Canonical STILL insists on compiling lm-sensors without the prober libsensors support.

You can fix that by downloading the source and compiling it yourself.

But, Ive found that the kernel parm works just as well.

---

### Post by sumithar on 2011-09-24
> **Mark Phelps said:**
> OK ... the kernel parm that might work is "acpi_enforce_resources=lax"

Add that to your Linux kernel parms in /etc/default/grub

Reboot and then see if sensors picks up more readings.

This happens because Canonical STILL insists on compiling lm-sensors without the prober libsensors support.

You can fix that by downloading the source and compiling it yourself.

But, Ive found that the kernel parm works just as well.

I added that line to grub and also ran the update-grub command as recommended.  No joy.

Neither does the sensors command work, nor does the option to display CPU temp show up in either KRell sensor or in System Monitor Indicator.

I think it's about time to throw in the towel, a lot of you wonderful people have spent a lot of time on my behalf.

---

### Post by sumithar on 2011-09-24
> **dino99 said:**
> from your post #12, it seems that lm-sensors cant identify your hardware sensors, so you might report against it:

ubuntu-bug lm-sensors

note: some hardware dont have sensors, or sometimes they are blacklisted by default ubuntu config, look at yours into: /etc/modprobe.d/blacklist.conf

on my system i use psensor

Thanks, I've posted a bug.  I looked in that file- nothing jumps out at me.  I've attached it, FWIW.

Rgds

---

