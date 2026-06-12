---
title: "Trouble with lm-sensors"
date: 2010-03-21
forum: General Help
---

### Post by conb123 on 2010-03-21
Hiya I am having a little bit of trouble with lm-sensors, I would like to be able to keep an eye on my cpu temperature but it is being reported with very unbelievable values. According to sensors-detect I am using an "ITE IT8720F Super IO Sensors". This board is a Gigbyte GA-P55M-UD2. Here is the output from sensors:-

```
connor@connor-desktop:~$ sensors
it8720-isa-0290
Adapter: ISA adapter
in0:       +1.30 V  (min =  +0.00 V, max =  +4.08 V)   
in1:       +1.57 V  (min =  +0.00 V, max =  +4.08 V)   
in2:       +3.33 V  (min =  +0.00 V, max =  +4.08 V)   
in3:       +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:       +0.10 V  (min =  +0.00 V, max =  +4.08 V)   
in5:       +3.14 V  (min =  +0.00 V, max =  +4.08 V)   
in6:       +0.13 V  (min =  +0.00 V, max =  +4.08 V)   
in7:       +2.14 V  (min =  +0.00 V, max =  +4.08 V)   
in8:       +3.25 V
fan1:     1300 RPM  (min =    0 RPM)                   
fan2:      538 RPM  (min =    0 RPM)                   
temp1:       +26°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp2:       +25°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp3:       +22°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
vid:      +0.313 V

```

I am pretty sure that my cpu temperature is temp3 because it increases under load but 22 celcius is much lower than what is reported in the bios and in windows so I am pretty sure it is incorrect. Does anyone know of a fix for this?

---

### Post by blueridgedog on 2010-03-21
If you just want to change the label, you should be able to do that by editing /etc/sensors3.conf and /etc/sensors.conf.  It may take some reading and searching to get the right section and the right syntax, but it should be possible.  The syntax of the configuration file is detailed on the man page for the file.  Here is a web version of it:  [http://linux.die.net/man/5/sensors.conf](http://linux.die.net/man/5/sensors.conf)

---

### Post by conb123 on 2010-03-22
Ok so I was able to set the labels using the configuration from the example sensors.conf in the lm-sensors package. However I am trying to set the sensor type to thermal diode because the example file mentioned doing that if the temperatures seem wrong but it is not reading them they are staying as thermistor. Here is my sensors.conf at the moment:

```
chip "it87-*" "it8712-*" "it8720-*"
 
    label in0 "VCore 1"
    label in1 "VCore 2"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "-12V"
    label in6 "-5V"
    label in7 "Stdby"
    label in8 "VBat"
 
    compute in3 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)
    compute in4 ((30/10) +1)*@  , @/((30/10) +1)
    compute in5 (7.67 * @) - 27.36  ,  (@ + 27.36) / 7.67
    compute in6 (4.33 * @) - 13.64  ,  (@ + 13.64) / 4.33
    compute in7 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)
 
    set temp1_type 3
    set temp2_type 3
    set temp3_type 3
 
    label temp1       "M/B Temp"
    label temp2       "CPU Temp"
```

---

