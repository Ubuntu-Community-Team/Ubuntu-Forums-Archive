---
title: "lack of fan control"
date: 2012-04-24
forum: General Help
---

### Post by JohnnyC35 on 2012-04-24
I have been trying to set up lm sensor according to [http://ubuntuforums.org/showthread.php?t=250025](http://ubuntuforums.org/showthread.php?t=250025)

I have a 3pin and a 4pin fan connected to the motherboard and have some control via the bios but find that "silent" mode isn't.. 

when I type pwmconfig I get 
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

but I thought there was a patch for that, but I can't find it.

sensors -s brings up
```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +22.0°C  (high = +70.0°C, crit = +90.0°C)
Core 1:       +29.0°C  (high = +70.0°C, crit = +90.0°C)

w83l771-i2c-0-4c
Adapter: SMBus nForce2 adapter at 4d00
temp1:        +34.0°C  (low  = -40.0°C, high = +70.0°C)
                       (crit = +85.0°C, hyst = +75.0°C)
temp2:        +52.8°C  (low  = -40.0°C, high = +70.0°C)
                       (crit = +110.0°C, hyst = +100.0°C)


```

and sensors-detect shows
```

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Driver `lm90':
  * Bus `SMBus nForce2 adapter at 4d00'
    Busdriver `i2c_nforce2', I2C address 0x4c
    Chip `w83l771' (confidence: 6)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
lm90
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!


```

I haven't found any new guides on this. they all seem to be before 10.04 so any help would be ... well... helpful :)

---

