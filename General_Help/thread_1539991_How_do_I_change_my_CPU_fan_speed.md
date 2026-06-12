---
title: "How do I change my CPU fan speed?"
date: 2010-07-27
forum: General Help
---

### Post by Arachan on 2010-07-27
Greetings,

In Windows (which I can happily say that I no longer have) I had a program called SpeedFan, which monitored the temperatures of my hardware and also my fan speeds. In Ubuntu I monitor my temperatures and fan speed through and AWN applet called Hardware Sensors; however I cannot find a program to change the fan speed. I think that it is just running at full speed in Ubuntu, I'm sure it was slower in Windows.

If anyone could help, that would be great.

Thanks,
Arachan.

---

### Post by dino99 on 2010-07-27
there is one called fancontrol (into synaptic)

---

### Post by wojox on 2010-07-27
[How To Control Fan Speeds in Ubuntu]("http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/")

Check your BIOS as well.

---

### Post by no2498 on 2010-07-27
install ( htop ) run it and see if something is wrong first

open a terminal type in, htop it tells you how to install it

type htop  see what is running to make the fan run fast

i use a flash chat and it hits my cpu at 80to 100%

depends on what browser i use i find the 1 that only goes to 16% and use it

hope this helps

---

### Post by Arachan on 2010-07-28
Greetings, 

Thanks for the swift replies. I tried fancontrol but I got an error: 

```
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file
```I had a look and there was no file. How would I make/get one?

I tried the tuxtweaks link and go up to the step:

```
sudo pwmconfig
```Where I got the error:

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```Even though I added the one that:

```
sudo sensors-detect
```found. How do I get it to recognise my fan? It's just the basic HSF for an Intel E2180. 

I also tried htop, but I couldn't see anywhere in it to manually change fan speeds. Could you point me in the right direction for that?

Thanks,
Arachan.

---

### Post by Arachan on 2010-07-29
Greetings, 

On a semi-related note, I noticed that my HD2600 fan is running at 100% all the time. How would I slow that down?

Thanks,
Arachan.

---

### Post by Arachan on 2010-08-04
Greetings,

I discovered the command 

```
aticonfig --od-gettemperature | grep Sensor | awk '{print "GPU: " $5 "C"}'
```displays the GPU temperature. The command 

```
sudo aticonfig --pplib-cmd "set fanspeed 0 20"
```sets the fan speed at 20% (what I run it at now). 

Arachan.

---

### Post by Arndt on 2010-08-04
> **Arachan said:**
> Greetings,

In Windows (which I can happily say that I no longer have) I had a program called SpeedFan, which monitored the temperatures of my hardware and also my fan speeds. In Ubuntu I monitor my temperatures and fan speed through and AWN applet called Hardware Sensors; however I cannot find a program to change the fan speed. I think that it is just running at full speed in Ubuntu, I'm sure it was slower in Windows.

If anyone could help, that would be great.

Thanks,
Arachan.

I use something called acpitool. I don't remember where I found it or why the others things I tried didn't work.

---

