---
title: "gps startup script"
date: 2010-05-11
forum: General Help
---

### Post by Directive 4 on 2010-05-11
ok i use gps with my laptop(10.04) 

gps don't work plug and play, because gpsd gets binded under nobody

a work around is to kill gpsd and start it up under your own login then upon starting tango gps works


so i want to make a shell script to do such things


[B]sleep 30 &&

ps -C gpsd -fww &

sudo kill the pid number

sleep 15 

gpsd -N -n -D 2 /dev/ttyUSB0 &[/B]

[B]exit
[/B]

seems a place to start, 

but maybe some grammer wrong. 

**question**

the command 

**ps -C gpsd -fww**

outputs

[B]UID        PID  PPID  C STIME TTY          TIME CMD
nobody     927     1  0 22:12 ?        00:00:00 /usr/sbin/gpsd -F /var/run/gpsd.
sock -P /var/run/gpsd.pid[/B]

does anyone know how to take the pid number from this output and feed it to the next command ie
**sudo kil*****l 927***

kind regards

---

### Post by dcstar on 2010-05-11
> **Directive 4 said:**
> 
.......
**ps -C gpsd -fww**

outputs

[B]UID        PID  PPID  C STIME TTY          TIME CMD
nobody     927     1  0 22:12 ?        00:00:00 /usr/sbin/gpsd -F /var/run/gpsd.
sock -P /var/run/gpsd.pid[/B]

does anyone know how to take the pid number from this output and feed it to the next command ie
**sudo kil*****l 927***

kind regards

```
man cut
```

---

### Post by bredman on 2010-05-11
The command
pkill gpsd
will kill the process named gpsd.

---

### Post by Directive 4 on 2010-05-11
thanks

---

