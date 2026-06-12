---
title: "Ubuntu start with peformance mode"
date: 2011-12-18
forum: General Help
---

### Post by javidemon95 on 2011-12-18
Ubuntu start with performance mode. I want it has ondemand by default. What can I do?

---

### Post by xyzzyman on 2011-12-18
Easiest way is to install Jupiter: 
[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

You can also always recompile your kernel and change the default to ondemand, but unless you are doing something else it's not worth the time although you do learn alot esp if you make a mistake.

---

### Post by pqwoerituytrueiwoq on 2011-12-18
it actually does start in preformace mode it switches to ondemand a minute later by default
install the boot-up manager and turn ondemand off
you can edit [FONT=Courier New]/etc/init.d/ondemand[/FONT] if you prefer

---

### Post by xyzzyman on 2011-12-18
He said he WANTS it in ondemand mode. That's mean telling him to turn it off. :P

---

### Post by pqwoerituytrueiwoq on 2011-12-19
opps thought he wanted it on performance mode
post output of these 2 commands
[FONT=Courier New]locate ondemand[/FONT]
[FONT=Courier New]cat /etc/init.d/ondemand | grep "echo -n"[/FONT]
EDIT:
If you have ondemand and just want it sooner edit [FONT=Courier New]/etc/init.d/ondemand[/FONT] locate the "sleep 60" change it to "sleep 30" and it will switch for ondemand sooner after boot

---

### Post by javidemon95 on 2011-12-19
> **pqwoerituytrueiwoq said:**
> opps thought he wanted it on performance mode
post output of these 2 commands
[FONT=Courier New]locate ondemand[/FONT]
[FONT=Courier New]cat /etc/init.d/ondemand | grep "echo -n"[/FONT]
EDIT:
If you have ondemand and just want it sooner edit [FONT=Courier New]/etc/init.d/ondemand[/FONT] locate the "sleep 60" change it to "sleep 30" and it will switch for ondemand sooner after boot
The first:
```
javier@javier-i7:~$ locate ondemand
/etc/init.d/ondemand
/etc/rc2.d/S99ondemand
/etc/rc3.d/S99ondemand
/etc/rc4.d/S99ondemand
/etc/rc5.d/S99ondemand
/usr/src/linux-headers-3.0.0-12-generic/include/config/cpu/freq/gov/ondemand.h
/usr/src/linux-headers-3.0.0-14-generic/include/config/cpu/freq/gov/ondemand.h
/var/lib/update-rc.d/ondemand
javier@javier-i7:~$ 

```
And the second
```
javier@javier-i7:~$ cat /etc/init.d/ondemand | grep "echo -n"
        echo -n ondemand > $CPUFREQ
javier@javier-i7:~$
```
Thanks for help me :) . What i need to do now?

---

### Post by xyzzyman on 2011-12-19
Are you manually changing it to ondemand mode? And how so? pqwoerituytrueiwoq is under the impression it's automatically doing it for you but I don't think that's the case. Did you manually change it since last boot? If so can you reboot, wait 10 minutes then run the second command and see what the result is?

---

### Post by javidemon95 on 2011-12-21
I change it with the cpu indicator in unity. If i change it and i reboot, the output is the same.

---

### Post by xyzzyman on 2011-12-22
Yeah. Without recompiling your kernel to change the default, Jupiter is your best bet. It'll save your settings across reboots. And it also turns on other power saving options.

---

### Post by dcstar on 2011-12-22
> **javidemon95 said:**
> Ubuntu start with performance mode. I want it has ondemand by default. What can I do?

Nothing. Wait 60 seconds and it will be in Ondemand.

If it stays in "Performance" mode then you have an application maxing out the CPU.

---

### Post by javidemon95 on 2012-01-08
@xyzzyman Thanks, but i don t want mono.
@dcstar Thanks, i will check it
EDIT: 
@dcstar: Still is in that mode. But it started when I installed cpu-indicator

---

