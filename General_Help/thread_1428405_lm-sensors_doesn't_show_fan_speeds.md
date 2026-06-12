---
title: "lm-sensors doesn't show fan speeds"
date: 2010-03-12
forum: General Help
---

### Post by Guest1234 on 2010-03-12
I'm running ubuntu 9.10 64 bit on a Dell Latitude E6400 with the following configuration:

Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz, 3MB L2 Cache 1066 MHz
Intel Graphics Media Accelerator x4500HD
4GB RAM
250 GB Hard Drive SATA 7200RPM

I'm experiencing overheating problems, after just 15-20 minutes of minimal use (surfing the internet, not even watching flash vids or any other vids).
The same laptop under Windows 7 64 bit stayed really cool.

I've read several posts here and followed this manual: [http://ubuntuforums.org/showthread.php?t=42737]("http://ubuntuforums.org/showthread.php?t=42737") 
to try to control the fans (I only installed the lm-sensors and ran the sensors command, I didn't do anything beyond that).
Specifically what I did was install lm-sensors (via apt-get), ran sensors-detect which advised me to add the coretemp module to /etc/modules, which I did.

However when running sensors the only information I get is the overall temperature and the temperature of each of the cores.

So my question is why I'm not getting fan speed info when running sensors?
Also is there a way to find out if more modules needs to be added to /etc/modules?

Thanks in advance,
Ido

---

### Post by fragos on 2010-03-12
did you run "sudo sensors-detect"? That is what queries your system for sensors and makes sure the correct drivers are loaded. You will need to reboot for all to occur correctly and then run "sensors".

---

### Post by Guest1234 on 2010-03-13
Yes I ran sensors-detect, rebooted and then ran sensors and the only readings I get are the overall temperature and each of the cpu core temperature.

Is there a way to find out which modules should be added to /etc/modules "manually" or in some other way?

* All these operations I ran as root of course.

---

### Post by DeMus on 2010-03-13
I have the same problem with Jaunty. And I dare to say it is not an Ubuntu error, it is a kernel error. When I installed Jaunty it worked, after a kernel update it stopped working. I believe the latest kernel version it still works, however I am not 100% sure about this, is 2.6.30. I now run 2.6.33 and also can not set my fans the way I want them to.
It seems that some module shave been taken out of the kernel and so fancontrol is not running anymore. It's a shame. My fans are on full speed and don't have to be with the things I do with my computer.
Anyone any idea how to change this?

---

### Post by fragos on 2010-03-13
This may not be your issue but I think fans have to be 4 wire to be speed controlled. I used a hardware fix for my case case -- basically an inline potentiometer designed for the purpose. The sensors can still read the change in RPM.

---

### Post by Guest1234 on 2010-03-13
You mean my hardware does not come with fan speed sensors?
How can I find out if that's the case?

The reason I want to check the fans speed is that in Ubuntu 9.10 64 bit the fan seems always on and in Windows 7 64 bit it only sporadically turns on.
Now I wouldn't mind that the fan is always on but ironically in Ubuntu the laptop is overheating. How could it be that when the fan is always on the laptop gets hotter and when it only sporadically runs in Windows 7 the laptop is cooler?

Is there a way based on the hardware specification I have to find out which modules needs to be added to /etc/modules so I can get fan speed readings?
Does anybody else have a Dell Latitude E6400 and know which modules should be added?

---

### Post by Mark Phelps on 2010-03-13
It's got nothing to do with your fans needing to have four wires.  Mine have three wires and report just fine.

what is has to do is with ACPI working differently in Karmic than its predecessors -- and that causing lm-sensors to not work anymore.

I was able to solve the same problem on my machine by doing the following:

"Add acpi_enforce_resources=lax to your grub configuration file."

Now realize, if you Google this, you'll see warnings against using this, but I've been doing it since Karmic came out on my machine (and I noticed that lm-sensors was no longer reporting fan speeds) and have encountered no problems whatsoever.

---

### Post by fragos on 2010-03-13
The purpose of sensors-detect is to identify your sensors both on the mobo and in devices. If you say yes when it offers it will enable the loading of the correct drivers. This works correctly for my Dell 1420n and my Desktop which has an Asrock mobo. No fan speed sensors were found on my Dell 1420 but you can hear the fan being turned on and off.

---

### Post by Guest1234 on 2010-03-13
I've added GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax" to my grub configuratio file and restarted my laptop.

After reboot I ran sensors-detect again, which only suggested me adding the "coretemp" module which I already have in /etc/modules.
I ran sensors again and still the only readings I get is the core temperatures.

Can I control the fan speed even if I don't have fan speed sensors?
I want to try to emulate the way the fans are working in windows (sporadically instead of all time as in ubuntu) so I can rule out that it's not the fans "behavior" that causes the overheating. 
Although I can't understand how preventing the fans from running all the time will reduce heat. (Maybe running the fans harder for short time periods is more optimal than running them all the time???)

---

### Post by fragos on 2010-03-13
My Dell has the fan input on the bottom which depending where I place it could obstruct air flow. What CPU temp reading are you getting. 40 degrees C for example is quite warm but well within operating range.

---

### Post by Mark Phelps on 2010-03-14
Heat problems are due to more than just fan speeds.  Modern CPUs commonly have the ability to scale back during idle times, thus running cooler. Your fans running all the time could be an indication that, in Ubuntu, your processor is not scaling back; thus, it's not getting a chance to cool down.

If you can monitor the CPU speed, you can watch for this.

If your CPU is running at full speed nearly all the time, you do not want to cut back on the fans ... you have a different problem than controlling fan speeds.

---

### Post by Guest1234 on 2010-03-14
I've added the "CPU Frequency Scaling" monitor to my Gnome panel and both cores are set to "on demand" governor, and unless I try to stress the computer they both stay at 800MHz and if I do stress them they reach to 2.5 GHz but afterwards scale back to 800MHz so it seems there isn't a frequency scaling problem.

I checked in Windows 7 and the results are the same, most of the time the cores are running at 800 MHz.
Yet I still hear the fans running all the time in Ubuntu, again this wouldn't bother me if there was no overheating problem.

This is the output of the sensors command:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +46.5°C  (crit = +107.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +40.0°C  (high = +100.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (high = +100.0°C, crit = +100.0°C)

```

Now I know some people wouldn't consider 46.5 C as an issue but I bought this laptop specifically because I read reviews that said it stays extremely cool and I know that in windows 7 it does stays cool (during normal use none of the cores temperature rise above 32 C).

So if you guys can think of some way of tweaking it to reach those results I'd appreciate it :)

PS
I've also tried setting to cores to conservative governor, no difference in results.

---

