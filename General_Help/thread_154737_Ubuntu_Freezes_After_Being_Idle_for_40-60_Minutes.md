---
title: "Ubuntu Freezes After Being Idle for 40-60 Minutes"
date: 2006-04-03
forum: General Help
---

### Post by gurjit on 2006-04-03
I was wondering, why does Ubuntu freeze after about an hour of being idle, or while im playing a game and leave it on for like 30 minutes. Could it be the ATI Drivers i installed (I think its called flxgr?). 

Thanks Alot For Any Help
Gurjit Bains

---

### Post by Jason_25 on 2006-04-03
Do you have an AMD cpu?  It may be the powernowd package that's causing the freezes.  You can remove it with no side effects.  The in game lockup may be caused by hardware problems or the ati drivers.

---

### Post by gurjit on 2006-04-03
I got a Crappy AMD Athalon, and where do i find that package u were talking about. powerown?

Thx for the reply btw

Gurjit

---

### Post by Jason_25 on 2006-04-03
Either through apt-get or synaptic, of course.

---

### Post by gurjit on 2006-04-03
[B][COLOR="Red"][B][B]> gurjit@UBUNTU:~$ sudo powernowd
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]
gurjit@UBUNTU:~$
[/B][/B][/COLOR][/B]


I get that error when i try to run powernowd, any ideas.
Also when i go to install the cpufreq, i can only find cpufreqd in the synaptic package manger available for download.

Thanks
Gurjit

---

### Post by henriquemaia on 2006-04-03
Try to shut down powernowd. Maybe it stops freezing your computer.

```
sudo /etc/init.d/powernowd stop
```

If that makes the trick, edit your init with BUM or some similar program and stop powernowd from the starting up during boot time.

---

### Post by gurjit on 2006-04-03
Thx for the reply, is it possible for me to delete powernowd from my system if it is the casue of the problem or will it cause some problems later on?

Thanks Alot
Gurjit Bains

---

### Post by henriquemaia on 2006-04-03
[QUOTE=gurjit]Thx for the reply, is it possible for me to delete powernowd from my system if it is the casue of the problem or will it cause some problems later on?

Thanks Alot
Gurjit Bains[/QUOTE]

As far as I know, there's no problem at all. I did that once when I was having some problems with my ubuntu box freezing too. 

You can remove it using synaptic. If you use BUM to make it stop running at boot time, you don't even need to remove it. It simply won't start. 

ps: My problems with freezing were due to excessive heat on the CPUs. My machine at that time was not properly cooled. If you still have problems, think about this.

---

### Post by gurjit on 2006-04-03
Thx for the reply.

I'll keep that in mind to make sure my cpu is cool enough but i dont think thats the problem since the side panel of my case is open there is alot of cool air getting in there :p 

Ok, one more question what is this BUM thing ur talking about, and how to i access it?

Gurjit Bains

---

### Post by henriquemaia on 2006-04-03
[QUOTE=gurjit]Thx for the reply.

I'll keep that in mind to make sure my cpu is cool enough but i dont think thats the problem since the side panel of my case is open there is alot of cool air getting in there :p 

Ok, one more question what is this BUM thing ur talking about, and how to i access it?

Gurjit Bains[/QUOTE]

From their site ([http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html))

"Boot-Up Manager is a Perl-Gtk2 application to handle runlevels configuration of any debian derivative system. With this program the user will easily start and stop boot-up scripts, without the necessity to handle thru complex links and permissions."

It's a GUI tool to select what services start on your machine. At boot time, ubuntu starts severall programs for different tasks. If you are on an AMD box, ubuntu starts powernowd as a default. 

You can install it through synaptic. It's available on the repositories.

---

### Post by gurjit on 2006-04-03
Ok, thx for the suggestion.

I downloaded BUM but its kinda slow; is this normal?

Thanks
Gurjit Bains

---

### Post by henriquemaia on 2006-04-03
[QUOTE=gurjit]Ok, thx for the suggestion.

I downloaded BUM but its kinda slow; is this normal?

Thanks
Gurjit Bains[/QUOTE]

Yes, on mine is slow also. If you think it's too slow, try installing rcconf. It is on the repositories also. It's a terminal app, very simple. I prefer rcconf, but BUM is more eye-candy.

---

