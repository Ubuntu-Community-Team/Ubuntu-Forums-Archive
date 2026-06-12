---
title: "fancontrol Elitebook 8460p ubuntu 11.04"
date: 2011-09-07
forum: General Help
---

### Post by TheTrueElling on 2011-09-07
My fan is running on 100% all the time.
Would appreciate help.

[I]$ sudo pwmconfig 
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

$ fancontrol
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file
elling@ellinghp:~$[/I]

sensors-detect gives the following summary

....
[I]Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Driver `max6650':
  * Bus `Radeon i2c bit bus 0x96'
    Busdriver `UNKNOWN', I2C address 0x1b
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)
  * Bus `Radeon i2c bit bus 0x96'
    Busdriver `UNKNOWN', I2C address 0x1f
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)
  * Bus `Radeon i2c bit bus 0x96'
    Busdriver `UNKNOWN', I2C address 0x48
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)
  * Bus `Radeon i2c bit bus 0x96'
    Busdriver `UNKNOWN', I2C address 0x4b
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)

Driver `sbs':
  * Bus `Radeon i2c bit bus 0x96'
    Busdriver `UNKNOWN', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

Warning: the required module sbs is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
max6650
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!
[/I]

Even after i have added the "coretemp" and "max6650" to /etc/modules i get the same result from sensors-detect.

---

### Post by Toz on 2011-09-09
Have you tried this: [http://ubuntuforums.org/showpost.php?p=10848757&postcount=2]("http://ubuntuforums.org/showpost.php?p=10848757&postcount=2")?

---

### Post by TheTrueElling on 2011-09-13
> **Toz said:**
> Have you tried this: [http://ubuntuforums.org/showpost.php?p=10848757&postcount=2](http://ubuntuforums.org/showpost.php?p=10848757&postcount=2)?
Nope, but now I have, it did not do the trick! Thanks for the info though!

---

