---
title: "How can I control fan speed? :("
date: 2012-09-11
forum: General Help
---

### Post by themirror178 on 2012-09-11
CPU: i7-2600k
Motherboard: Gigabyte P67A-UD3R
Ubuntu 12.10

I can only see the temperatures, no fan speeds and can't change anything. I've made sure in the BIOS it's set to PWM. I can control the fan speed in Windows 7 using gigabyte fan utility.

Here's the output of sensors-detect:


```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `ITE IT8728F Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Note: there is no driver for ITE IT8728F Super IO Sensors yet.
Check http://www.lm-sensors.org/wiki/Devices for updates.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

```

Does that mean there's no fan control for my cpu? Or am I doing something wrong?

Thanks

---

### Post by spaceshipguy on 2012-09-11
Perhaps you need the fan and temperature is your problem. Is your computer too hot? Installing Jupiter from the software centre cooled my laptop from 80 degrees to 50 degrees. My fan is a lot quieter now.

---

### Post by rawlins02 on 2012-09-11
methods for controlling the system fan:

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

---

### Post by themirror178 on 2012-09-12
> **rawlins02 said:**
> methods for controlling the system fan:

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

Isn't that for thinkpads lenovo/ibm?

I'm using a custom built pc with a gigabyte motherboard...intel i7 2600k cpu

---

### Post by themirror178 on 2012-09-22
Well I figured it out after hours of searching. Hopefully this will help someone.

install lmsensors and run sensors-detect from command line. It wont find the it87 driver, so you have to manually install it. Type each of the lines below: 

```
sudo -s
mkdir /usr/src/it87
cd /usr/src/it87
wget http://khali.linux-fr.org/devel/misc/it87/Makefile
wget http://khali.linux-fr.org/devel/misc/it87/it87.c
make
make install

echo "it87" >> /etc/modules

modprobe it87

pwmconfig (NOW this should detect the it87 super io sensors)
```Source: [http://mark.orbum.net/2012/05/20/get-lm-sensors-working-with-asus-m5a996x-evo-motherboard/](http://mark.orbum.net/2012/05/20/get-lm-sensors-working-with-asus-m5a996x-evo-motherboard/) (says asus but drivers work for gigabyte too) Configure your fans as you wish.

---

