---
title: "control - alt - delete ? equivalent"
date: 2011-05-17
forum: General Help
---

### Post by kevinorourke2008 on 2011-05-17
Hi Guys, 
I've tried looking for this info but can't find it anywhere. I am running ubuntu 9.04 on my netbook and sometimes (very rarely) it freezes, if this happened in windows I would use the control - alt -  delete to get out of the situation, is there an equivalent in Ubuntu ?

Cheers kev

---

### Post by linuxman94 on 2011-05-17
When you say that it freezes, do you mean the application or the entire system?  If it is the system then you just have to hold the power button until it turns off.  I would update to 10.04 because 9.04 is no longer supported.

---

### Post by dragonfly41 on 2011-05-17
I'm not sure if this is in your ubuntu 9.04

but in unbuntu 10.10

System > Administration > System Monitor > Processes > right click to end or kill process

---

### Post by WorMzy on 2011-05-17
Ctrl+Alt+F1 will switch you to a tty where you can log in and kill the offending process (if you know what it is).

```
killall <processname>
```

If you can't switch to a tty, then try the "Magic SysRq" keys:

Hold down Ctrl+Alt+SysRq and press R - E - I - S - U - B, leaving a slight pause between each key.

If that doesn't safely reboot your system, then your only other option is a hard reset,like Linuxman suggested.

---

### Post by zealibib slaughter on 2011-05-17
see this thread ubuntuforums.org/showthread.php?t=1740183

---

