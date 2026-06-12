---
title: "push cpu up to max without cpufreq?"
date: 2011-01-31
forum: General Help
---

### Post by qwertyjjj on 2011-01-31
I am having some problems with my CPU speed detailed here:
[https://answers.launchpad.net/ubuntu/+source/acpi/+question/143039](https://answers.launchpad.net/ubuntu/+source/acpi/+question/143039)

Basically it is restricting my computer to 800Mhz after 10-15mins for no reason. With Windows I was able to use something called Notebook Hardware control to ramp up the speed to the max of 1.73GHz. With the cpufreq applet, it won;t do anything.

Is there another program I can use to override the speed?

---

### Post by qwertyjjj on 2011-02-03
any ideas?
can't find other cpu programs

---

### Post by cascade9 on 2011-02-03
I'll give you the same answer as last time....

> **qwertyjjj said:**
> I changed it to performance and on demand and nothing.
Loaded FF plus some other programs and it doesn't budge from 800.
I had the same problem on Windows and for that I had to use something called Notebook Hardware control to ramp up the CPU manually.


Probably a hardware error, dont blame ubuntu for that. If its not a hardware error, I'd guess its a BIOS problem. Could be either the BIOS setings used or some other more esoteric BIOS problem. 

> **qwertyjjj said:**
> any ideas why the speed switch would stop working?

j@j-Inspiron-9300:~$ sudo modprobe p4_clockmod
[sudo] password for j: 
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.35-24-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): Device or resource busy
-Inspiron-9300:~$ nano /etc/modules
-Inspiron-9300:~$ nano /etc/modules
-Inspiron-9300:~$ p4_clockmod
p4_clockmod: command not found
-Inspiron-9300:~$ sudo cpufreq-selector -f 1000000
-Inspiron-9300:~$ sudo cpufreq-selector -f 1070000
-Inspiron-9300:~$ sudo cpufreq-selector -f 1070000
-Inspiron-9300:~$

What on earth made you install P4 clockmod? 

IIRC P4 clockmod was only made for P4s, they had horrible power control. Its liable to just make things worse on non-P4 CPUs.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1674898](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1674898)

---

### Post by qwertyjjj on 2011-02-04
> **cascade9 said:**
> I'll give you the same answer as last time....



Probably a hardware error, dont blame ubuntu for that. If its not a hardware error, I'd guess its a BIOS problem. Could be either the BIOS setings used or some other more esoteric BIOS problem. 



What on earth made you install P4 clockmod? 

IIRC P4 clockmod was only made for P4s, they had horrible power control. Its liable to just make things worse on non-P4 CPUs.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1674898](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1674898)

I was given a post that said it was a problem on Inspiron computers and that the p4 clock mod should be used instead.
How can I uninstall it?
Does this do it?
j@-Inspiron-9300:~$ sudo modprobe acpi-cpufreq
[sudo] password for jason: 
j@-Inspiron-9300:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
 


I don't really understand why NHC on Windows could push it up to 1.73 yet cpufreq on Linux cannot though?

---

### Post by TBABill on 2011-02-04
Did you try it manually with CPUFREQ? You can find out what it is set to by doing the following in a terminal: ```
cpufreq-info
``` and the text in quotes is your current setting. If you want to change it to max performance, just ```
sudo cpufreq-set --governor performance
``` Then run the first command again to verify it took.

---

### Post by dcstar on 2011-02-05
> **qwertyjjj said:**
> I am having some problems with my CPU speed detailed here:
[https://answers.launchpad.net/ubuntu/+source/acpi/+question/143039](https://answers.launchpad.net/ubuntu/+source/acpi/+question/143039)

Basically it is restricting my computer to 800Mhz after 10-15mins for no reason.
.......

"No reason", **exactly** how hot is the CPU then?

---

### Post by qwertyjjj on 2011-02-05
> **TBABill said:**
> Did you try it manually with CPUFREQ? You can find out what it is set to by doing the following in a terminal: ```
cpufreq-info
``` and the text in quotes is your current setting. If you want to change it to max performance, just ```
sudo cpufreq-set --governor performance
``` Then run the first command again to verify it took.

When I change it to that on the gnome panel, it pushes it up to 1.72GHz but only first thing when I turn the computer on. 

> **dcstar said:**
> "No reason", **exactly** how hot is the CPU then?

I have posted the results below.
It took about 25mins before the givernor throttled the speed back. The full fan speed did not even come and now I cannot change it back to 1.73.
The fan successfully controlled the temperature down so why throttle it afterwards?
I am running a video, FF, Thunderbird, a disk usage analyser, and system testing util to try and load it. The fan only comes on at above 60oC and even then it's only half fan speed (fairly quiet), not the full fan speed that I had in the past on Windows.
So, how come when it is set to ondemand, it throttles it to 800 when it gets to this temperature and prevents me from changing it to performance?
Do I need to compile speedstep-centrino?
The main question I have is that if this is an overheating problem, why does the fan not come on at full speed and also, why when the temp has dropped back to the 40s does it not increase the speed back up to 1.73? High 60oC seems about normal for this computer.

```

j@j-Inspiron-9300:~$ sudo cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: [B]frequency should be within 800 MHz and 1.73 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.[/B]
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 1.73 GHz:28.76%, 1.33 GHz:1.14%, 1.07 GHz:1.28%, 800 MHz:68.83%  (6017)

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:20:04 CET 2011
j@j-Inspiron-9300: cat /proc/acpi/thermal_zone/THM/temperature
temperature:             39 C

**{switched to performance in the middle here}**
{now fully on 1.72GHz}
j@j-Inspiron-9300:/$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: **frequency should be within 800 MHz and 1.73 GHz**.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.
  cpufreq stats: 1.73 GHz:49.04%, 1.33 GHz:0.71%, 1.07 GHz:0.81%, 800 MHz:49.44%  (8722)


j@j-Inspiron-9300:/$ date
Sat Feb  5 10:29:33 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             45 C

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:32:14 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             56 C

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:33:51 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             57 C

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:35:25 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             56 C

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:37:58 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             62 C

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:39:41 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             65 C
**{half fan speed comes on here but not full speed yet}**

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:43:14 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             57 C

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:44:32 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             59 C

j@j-Inspiron-9300:/$ date
Sat Feb  5 10:46:22 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             69 C
** {half fan on again}**
[B]
{throttled back here to 800 and will not increase}[/B]
j@j-Inspiron-9300:/$ date 
Sat Feb  5 10:51:45 CET 2011
j@j-Inspiron-9300:/$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             43 C

j@j-Inspiron-9300:/$ cpu-freq info
cpu-freq: command not found
j@j-Inspiron-9300:/$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: [B]frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.[/B]
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.73 GHz:62.92%, 1.33 GHz:0.40%, 1.07 GHz:0.45%, 800 MHz:36.22%  (8723)

**{turned computer off for 5mins here}**
j@j-Inspiron-9300:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             34 C
**still throttled to 800.**








```

---

### Post by cascade9 on 2011-02-05
@ dcstar- I was actually thinking that it could be possible that this was temprature related. After having a think about it, reading those CPU temps I dont think it is and reading the 'fan runs slower in linux' I dotnthink it is (if it was temp related it shouldnt be as bad in windows as it is with linux) . 

@ qwertyjjj- if you have a problem with both windows and linux, its very unlikely to be software related. Trying to find a software fix for hardware/BIOS problems probably wont help, and can make things worse. 

I'd try cleaning out all the vents, and flashing the BIOS to the newest version. You might need to figure out how to strip P4clockmod, or try a liveCD after flashing the BIOS.

---

### Post by qwertyjjj on 2011-02-05
> **cascade9 said:**
> @ dcstar- I was actually thinking that it could be possible that this was temprature related. After having a think about it, reading those CPU temps I dont think it is and reading the 'fan runs slower in linux' I dotnthink it is (if it was temp related it shouldnt be as bad in windows as it is with linux) . 

@ qwertyjjj- if you have a problem with both windows and linux, its very unlikely to be software related. Trying to find a software fix for hardware/BIOS problems probably wont help, and can make things worse. 

I'd try cleaning out all the vents, and flashing the BIOS to the newest version. You might need to figure out how to strip P4clockmod, or try a liveCD after flashing the BIOS.

So, this won't do the job? sudo modprobe acpi-cpufreq

I just checked DELL and the only bios they have is from 2005.

---

### Post by cascade9 on 2011-02-05
You can try whatever software you want, and its even possible you might find some workaround. But the basic problem will still be there...and the more mods/hacking you do, the harder it will be to figure out if you even have solved the problem. 

I think you already might be past that point, unless you can remove P4 clockmod, and possibly any other hacks you've done.

---

### Post by qwertyjjj on 2011-02-05
> **cascade9 said:**
> You can try whatever software you want, and its even possible you might find some workaround. But the basic problem will still be there...and the more mods/hacking you do, the harder it will be to figure out if you even have solved the problem. 

I think you already might be past that point, unless you can remove P4 clockmod, and possibly any other hacks you've done.

Isn't there something simple to remove the p4 clockmod?
modprobe remove or something?
Or simply replace it, shouldn't that acpi call above replace it completely?

So, I cleaned out the heatsink - it was completely blocked with dust.
My BIOS is Inspiron 9300 BIOS Revision A05

The half fan comes on now for 20seconds at about 50oC and seems to control the temp better.
I have the followiung running: VLC, FF, Thunderbird, VirtualBox with XP.
When the fan comes on it drops the temp to 43oC.
So, average temps are between 45 and 60.
Is there anyway the BIOS might be throttling the speedstep when the temp gets above 70 and then not letting it go above 800? Should it do that? I would have thought when the temp got lower it would let it go up again.

When running all these programs above, the fan will come on again every 2 mins or so - normal? Personally, I didn't think 70oC was high enough to cause a throttling of the speed.

---

### Post by qwertyjjj on 2011-02-05
> **qwertyjjj said:**
> Isn't there something simple to remove the p4 clockmod?
modprobe remove or something?
Or simply replace it, shouldn't that acpi call above replace it completely?

So, I cleaned out the heatsink - it was completely blocked with dust.
My BIOS is Inspiron 9300 BIOS Revision A05

The half fan comes on now for 20seconds at about 50oC and seems to control the temp better.
I have the followiung running: VLC, FF, Thunderbird, VirtualBox with XP.
When the fan comes on it drops the temp to 43oC.
So, average temps are between 45 and 60.
Is there anyway the BIOS might be throttling the speedstep when the temp gets above 70 and then not letting it go above 800? Should it do that? I would have thought when the temp got lower it would let it go up again.

When running all these programs above, the fan will come on again every 2 mins or so - normal? Personally, I didn't think 70oC was high enough to cause a throttling of the speed.

Spoke too soon!
Something is still turning it off after 15-30mins.
I reinstalled cpufreqd also so doubt it is a module problem now.

```

jason@jason-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: [B]frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range[/B].
  current CPU frequency is 800 MHz.

```

---

### Post by qwertyjjj on 2011-02-05
Is there a program like Windows' Notebook Hardware Control that can push the speed up and keep it there?

---

### Post by dino99 on 2011-02-05
uninstall powersaving settings under ubuntu, and dont forget to set bios settings as you want .

---

### Post by qwertyjjj on 2011-02-05
> **dino99 said:**
> uninstall powersaving settings under ubuntu, and dont forget to set bios settings as you want .

Remove System-->Preferences-->Power Management?
Ubuntu says if I uninstall Power management then future updates to the ubuntu desktop system module will not be installed.
My BIOS only has the speedstep option and that has to be enabled for it to work otherwise it restricts the computer to 800.
The strabge thing is is that once the computer has been throttled to 800, even restarting does not fix it. I need to shutdown, wait a few minutes and then restart, then it works for 15-30mins or so until it randomly shuts off. It's not like the CPU even gets hot now that I have cleaned the vent so it could only be something in the hardware or something wrong with cpufreq.

---

### Post by wojox on 2011-02-05
See here [Configuring cpu scaling to set to ondemand upon reboot]("http://ubuntuforums.org/showpost.php?p=10430563&postcount=22")

---

### Post by qwertyjjj on 2011-02-05
> **wojox said:**
> See here [Configuring cpu scaling to set to ondemand upon reboot]("http://ubuntuforums.org/showpost.php?p=10430563&postcount=22")

Thanks.
I tried that and set it to performance but when restarted it is still stuck at 800. Even though I select 1.73, 1.33, or 1.03 none of them work and it remains at 800.
Will removing cpufreq help?

---

### Post by qwertyjjj on 2011-02-05
I found this in the cpufreqd.conf:

##
# Special Rules
##
# CPU Too hot!
[Rule]
name=CPU Too Hot
acpi_temperature=55-100
cpu_interval=50-100
profile=Performance Low
[/Rule]

Could that be the problem?

Edit: I changed that to 70 and it still doesn;t work.
Something is changing the  scaling_max_freq file back to 800000 even though I changed it to 1733000 manually.
I just went in and edited the file back to 1733000 but when I next open it it has changed back to 800000. 
That to me seems like a cpufreq bug?!

How can I check if powersaving is turned off?

---

### Post by cascade9 on 2011-02-06
*sigh*

qwertyjjj, did you actually read anything I've written? 

I said I doubt that its temprature related (though hearing that you had a heatsink completely stuffed with dust does make me wonder if its possible for the TM1 or TM2 to get 'burnt' at all). 

The Pentium Ms should have a higher thermal throttling temp than 70c, but not by much, and there are major problems with some of the snesors of about the same age as your CPU- 

> The low accuracy of these sensors is well known, to be more exact, their great spread of shifts, it may reach even +/-20°C(!). [http://ixbtlabs.com/articles2/cpu/intel-thermal-features-pm.html](http://ixbtlabs.com/articles2/cpu/intel-thermal-features-pm.html)

ITS NOT ACPUFREQ 'BUG'! Windows doesnt use cpufreq, and you were having the same problem there. 

You should be able to remove p4 clockmod, but just reloading cpufreq or power management may not do it....

It doesnt matter if the last BIOS released for yourcomputer is from 2005, if its a newer version it may help.

---

### Post by qwertyjjj on 2011-02-06
> **cascade9 said:**
> *sigh*

qwertyjjj, did you actually read anything I've written? 

I said I doubt that its temprature related (though hearing that you had a heatsink completely stuffed with dust does make me wonder if its possible for the TM1 or TM2 to get 'burnt' at all). 

The Pentium Ms should have a higher thermal throttling temp than 70c, but not by much, and there are major problems with some of the snesors of about the same age as your CPU- 

[http://ixbtlabs.com/articles2/cpu/intel-thermal-features-pm.html](http://ixbtlabs.com/articles2/cpu/intel-thermal-features-pm.html)

ITS NOT ACPUFREQ 'BUG'! Windows doesnt use cpufreq, and you were having the same problem there. 

You should be able to remove p4 clockmod, but just reloading cpufreq or power management may not do it....

It doesnt matter if the last BIOS released for yourcomputer is from 2005, if its a newer version it may help.

I read what you wrote, it just seemed coincidental that when the temp got to above 60 that it was throttled but that doesn't seem to be it.
I have posted on the cpufreqd mailing list so will see what they suggest.
Thanks for your help, I will post back here when updated.

A05 is the latest BIOS for the Inspiron, last updated 2005.

---

### Post by dino99 on 2011-02-06
seems that the easiest, safest way, is to make a fresh reinstall

---

### Post by qwertyjjj on 2011-02-06
So, we tried turning off cpufreqd with /etc/init.d/cpufreqd stop
After 25mins, the speed was still throttled to 800.
I do not have cpudyn, cpuspeed, or powernowd installed.
So, what else could it be?

---

### Post by qwertyjjj on 2011-02-07
I also tried this as it was throttled down to 800 and it did not change:
I tried this after it was throttled down to 800 and it does not change the speed:
j@j-Inspiron-9300:~$ sudo cpufreq-set -u 1733000
j@j-Inspiron-9300:~$

So, is there any powersaving utility in Ubuntu that might do this?
Is there some other software that I can use to ramp up the CPU?
Is there any way I can track what throttles it down? If it is speedstep, I am not sure why as it is not overheating. I cannot turn off speedstep as then the whole system remains at 800 and cannot be ramped up.

----------

The problem I have is that Notebook Hardware control on Windows was able to push it up to 1.73 - maybe it did this through voltage control or something. Under Linux, there does not seem to be a similar porgram.
So, what are my options as I really do not want to use Windows on the laptop anymore.
Do I have to overclock it or something?

---

### Post by cascade9 on 2011-02-08
> **qwertyjjj said:**
> So, we tried turning off cpufreqd with /etc/init.d/cpufreqd stop
After 25mins, the speed was still throttled to 800.
I do not have cpudyn, cpuspeed, or powernowd installed.
So, what else could it be?

I've said it before- if you have the exact same issue on windows and on linux, its not a software problem (unless you want to count the BIOS as software)

You have been doing this plugged in, right? IIRC sometimes laptops/netboks can get slowed if you are running on battery power only.

---

