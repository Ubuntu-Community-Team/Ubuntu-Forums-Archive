---
title: "Temperature Program"
date: 2010-06-22
forum: General Help
---

### Post by COKEDUDE on 2010-06-22
I'm looking for a Temperature Program. My computer always feels really hot when running Linux, I would like a program that could help regulate temperature.

---

### Post by Rubi1200 on 2010-06-22
Not sure if this is what you are looking for, but I thought you might be interested anyway:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by jesuisbenjamin on 2010-06-22
Temperature should be regulated by BIOS if i am not wrong. Not by the operating system.
There are programs to return the temperature of your computer however. One such program is hddtemp.

To read the temperature of your hd you can for instance run:
```
sudo hddtemp /dev/sda
```

if your HD is at 60°C then there is a problem. Normally a hd's temperature is round 30°C to 40°C

---

### Post by COKEDUDE on 2010-06-22
```
sudo hddtemp /dev/sda
/dev/sda: Hitachi HTS721010G9SA00: 43°C

```
That looks good right now. 

It looks like I didn't explain what I wanted very well. In windows there are several programs that you can use to increase your fan speed after your computer reaches a certain temperature. I was hoping there was a similar program in Linux. Does anyone know of this type of program?

---

