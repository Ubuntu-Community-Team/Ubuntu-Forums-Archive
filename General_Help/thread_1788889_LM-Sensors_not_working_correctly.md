---
title: "LM-Sensors not working correctly"
date: 2011-06-23
forum: General Help
---

### Post by FinalShot on 2011-06-23
First of all I followed [this](https://help.ubuntu.com/community/SensorInstallHowto) to install lm-sensors. After I run sensors-detect, I get this output:
```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `max6650':
  * Bus `NVIDIA i2c adapter '
    Busdriver `nvidia', I2C address 0x4b
    Chip `Maxim MAX6650/MAX6651' (confidence: 2)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
max6650
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

```

sensors:
```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

I'm running a 2500k, P8P67 EVO B3 motherboard. I guess the P67 chipset might not be supported.

Any help is appreciated.

---

### Post by pqwoerituytrueiwoq on 2011-06-23
[http://ubuntuforums.org/archive/index.php/t-345710.html](http://ubuntuforums.org/archive/index.php/t-345710.html)
that may help

---

### Post by psusi on 2011-06-23
Did you follow the directions sensors-detect gave you, and then reboot?

---

