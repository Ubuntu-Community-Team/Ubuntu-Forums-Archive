---
title: "fan control (pwmconfig) doesnt work"
date: 2010-09-13
forum: General Help
---

### Post by maxx11 on 2010-09-13
Hi there. Im trying to set up fan control with lm-sensors and pwmconfig. Im using Ubuntu Server 10.04 so I cant use any of gui tools.

lm-sensors works fine. I can see many info thru it:
```

makk@serv:~$ sensors
as99127f-i2c-0-2d
Adapter: SMBus PIIX4 adapter at e800
in0:         +1.81 V  (min =  +1.54 V, max =  +1.95 V)   
in1:         +2.61 V  (min =  +2.24 V, max =  +2.74 V)   
in2:         +3.54 V  (min =  +2.96 V, max =  +3.62 V)   
in3:         +2.94 V  (min =  +2.67 V, max =  +3.26 V)   
in4:         +3.22 V  (min =  +2.40 V, max =  +3.58 V)   
in5:         +2.96 V  (min =  +2.42 V, max =  +3.62 V)   
in6:         +3.46 V  (min =  +2.66 V, max =  +3.98 V)   
**fan1:       3629 RPM  (min =    0 RPM, div = 4)**
**fan2:       2743 RPM  (min =    0 RPM, div = 4)**
fan3:          0 RPM  (min =    0 RPM, div = 4)
temp1:       +27.0°C  (high = +105.0°C, hyst =  +0.0°C)  
temp2:       +17.0°C  (high = +122.0°C, hyst = +121.0°C)  
temp3:       -31.5°C  (high = +122.0°C, hyst = +121.0°C)  
cpu0_vid:   +1.750 V
beep_enable:enabled
```
But runnig pwmconfig gives me nothing:
```

makk@serv:~$ sudo pwmconfig
# pwmconfig revision 5770 (2009-09-16)
/usr/local/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
Its strange because I could control both fans thru SpeedFan in Windows.

At last my 'sudo sensors-detect' output (did this before pwmconfig of course, as described in many howtos).
```

Driver `w83781d':
  * Bus `SMBus PIIX4 adapter at e800'
    Busdriver `i2c_piix4', I2C address 0x2d
    Chip `as99127f' (confidence: 6)
```

So my questions are:

1) Is there any official pwmconfig site? Cant find any...
2) Are there any solutions for my pwmconfig?
3) Are there any alternatives of pwmconfig for command line. (I know that is working because SpeedFand does this well in Windows!).

---

