---
title: "Monitoring programs"
date: 2012-05-12
forum: General Help
---

### Post by loseby on 2012-05-12
After something that will monitor my temps..... CPU , Harddrives etc etc ?

Also is there a good little program that will display info of my system ie. motherboard type, hard drives, memory type ?

[http://www.cpuid.com/]("http://www.cpuid.com/") works good on windows and am after something similar..... I dont really want to run them in that windows emulator program ( the name escapes me )

---

### Post by idoitprone on 2012-05-12
> **losbey said:**
> After something that will monitor my temps..... CPU , Harddrives etc etc ?

Also is there a good little program that will display info of my system ie. motherboard type, hard drives, memory type ?

[http://www.cpuid.com/](http://www.cpuid.com/) works good on windows and am after something similar..... I dont really want to run them in that windows emulator program ( the name escapes me )

I only know a few

```
top
```will monitor cpu and memory usage

lm-sensors will monitor cpu temp

```
sudo apt-get install lm-sensors
```lshw


or dmidecode will give system info

or you can

get cpu and ram info in the proc directory
```

cat /proc/cpuinfo
cat /proc/meminfo
```

---

### Post by oldos2er on 2012-05-12
For system info, open a terminal and run ```
sudo lshw > lshw.txt && gedit lshw.txt
```

---

### Post by Mopar1973Man on 2012-05-12
You might consider Conky...
[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

VinDSL did a awesome job of making a script to display quite a bit of information on the screen. ;)

---

### Post by jadtech on 2012-05-12
using psensor and conky  either of then work well though  for some reason this HP  has no fan speed sensors though can see processor temp and HD temp  ...

---

