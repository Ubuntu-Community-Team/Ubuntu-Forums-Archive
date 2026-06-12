---
title: "What is changing my CPU frequency?"
date: 2009-09-01
forum: General Help
---

### Post by Lockheed on 2009-09-01
I am trying to use cpupowerd to manage my voltages and frequency, but it notoriously quits with an error because some other program is also changing frequency.

How do I find and disable this program?

---

### Post by sefs on 2009-09-01
AMD Quiet 'n' Cool? or Intel's equivalent.  Check the bios to see if they are enabled.  They usually drop the frequency when the chip is not loaded with lots of work.

---

### Post by Lockheed on 2009-09-01
I dont have such option in bios. I am running laptop with Turion X2.

---

### Post by gradinaruvasile on 2009-09-01
> **Lockheed said:**
> I am trying to use cpupowerd to manage my voltages and frequency, but it notoriously quits with an error because some other program is also changing frequency.

How do I find and disable this program?

First, look in the BIOS.

---

### Post by P4man on 2009-09-01
The kernel probably already manages your clockspeed; To find out, just add "cpu freq scaling monitor" to your panel. If you get various options, and you see it change speed depending on load, the kernel is already doing it.

---

### Post by Lockheed on 2009-09-01
> **P4man said:**
> The kernel probably already manages your clockspeed; To find out, just add "cpu freq scaling monitor" to your panel. If you get various options, and you see it change speed depending on load, the kernel is already doing it.

It appears it does. How do I stop it from doing so?

---

### Post by P4man on 2009-09-01
why do you want to stop it? You can use it to clock your system up or down, and it will manage the voltages for you. most ppl post here how to enable it, not disable it :)

---

### Post by Lockheed on 2009-09-01
Because the only way to undervolt Turion X2 I know about is using cpupowerd which will not work of something else is interfering with frequencies.

---

### Post by P4man on 2009-09-01
try:

```
sudo killall powernowd
```

---

### Post by Lockheed on 2009-09-01
> **P4man said:**
> try:

```
sudo killall powernowd
```

I think powernowd is not running
```
powernowd: no process killed

```

---

### Post by P4man on 2009-09-01
hmm.. Im not sure what process is governing your cpu then, I guess you could try this:

[http://www.rob-ward.co.uk/thisarticle.php?id=5](http://www.rob-ward.co.uk/thisarticle.php?id=5)

---

### Post by Lockheed on 2009-09-04
Most of the time cpupowerd works fine. It lowers 800Mhz voltage 0.8V -> 0.75V and 1600Mhz voltage from 1.1V -> 0.9V

The problem is, that when system load is really heavy, for example very CPU intensive wine application, the voltage goes up to 1.1V regardless of cpupowerd.

What can be the culprit?

---

### Post by Lockheed on 2009-09-08
Bump...

---

### Post by Lockheed on 2009-09-27
Help. I did everything I know to find the culprit but something still changes the cpu frequency.

---

### Post by renkinjutsu on 2009-09-27
at bootup, a script called 'ondemand' is ran, and it changes your cpu frequency governor to ondemand.. the script's location: `/etc/init.d/ondemand`
to prevent it from starting on boot (without deleting it) do ```
sudo mv /etc/init.d/ondemand /etc/init.d/\!ondemand
```
that should do the trick

to check what it is right now: ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
to change it, you can get root privileges with ```
sudo -s
``` or ```
sudo su
``` beforehand, since good 'ol sudo <command> wouldn't work in this case.

then just echo whatever scaling governor you want into that file

```
echo -n performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
if you have 2 cores, you can repeat that step replacing `cpu0` with `cpu1`

---

### Post by Lockheed on 2009-09-27
The governor I get from *cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor* is "userspace"


I did ```
sudo mv /etc/init.d/ondemand /etc/init.d/\!ondemand
```
but it didn't help.

I have cpupowerd set to keep the voltage at 0.75v for 800Mhz and 0.9v for 1600Mhz. Most of the time, it does its job. However, if there is really heavy CPU load involved, for example several instances of "cat /dev/urandom > /dev/null", the voltage goes to stock 1.1V at 1600Mhz and after short while cpupowerd quits due to its built-in mechanism that causes it to quit when something else is changing cpu clock/voltage.

---

### Post by renkinjutsu on 2009-09-27
hmm .. try playing with the different values that go into ```
 /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
userspace ondemand performance conservative

infact, you seem to be looking for conservative or ondemand anyway.. i don't know how it effects the voltage though, but it keeps the cpu frequency at the lowest setting until you need it (even that saves power too)

---

### Post by philinux on 2009-09-27
**userspace ondemand performance conservative powersave**

Only 2 of the above governors dont change the freq. Namely performance, full speed ahead, and powersave, full slow.


See my last post.

[http://ubuntuforums.org/showthread.php?t=1274455](http://ubuntuforums.org/showthread.php?t=1274455)

---

### Post by Lockheed on 2009-09-27
I think we have a little misunderstanding here. I don't want to use any governors. Not even those that keep the freuency constant. 

I need to disable everything that affects frequency so that cpupowerd may do its job of being the sole manager of frequencies and voltages.

---

### Post by Lockheed on 2009-09-29
up

---

### Post by cguy on 2009-09-29
Dude, the inbuilt frequency scaler already lowers the frequency AND undervolts the CPU. And it modifies them @factory defined, safe levels.

You want to replace application A with application B which does the exact same job just because it's named A, not B?

---

### Post by Lockheed on 2009-09-29
As far as I know there is no other ways to underwolt Turion X2 other than cpupowerd.
Feel free to elight me if I'm in the dark.

---

### Post by Lockheed on 2010-02-04
Something still overrides voltage settings of cpupowerd and I have no idea what is that.

Any thoughts on the subject welcomed.

---

### Post by Lockheed on 2010-04-05
UP

As stated above.

---

### Post by Lockheed on 2010-06-29
H
ee
lll
pppp
!!!!!

---

