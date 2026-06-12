---
title: "How do I....Undervolt newer Turions?"
date: 2009-10-16
forum: General Help
---

### Post by Turk4n on 2009-10-16
I have a dv6 1110eo.
And the temps are really high for doing nothing !
I compared the heat generated in Ubuntu vs Windows 7.
***_Windows 7._***
**Idle**
39
**Load**
56
**Full load**
74
*_**Ubuntu 9.04. **_*
**Idle**
66
**Load**
74 
**Full load**
89
The temps are in celsius and with full load I mean of course not gaming load... or such thing, gaming will result the laptop shuts off also why game when you can program and read novels and play visual novels?. *Why this huge amount of fail?*
I didn't except it to be this bad, so wondering is it possible to undervolt the Turion X2 64 RM-74 2.2GHz CPU?
Current voltage, is P0 1.125v, P1 1.0v, P2 0.9v
P0 = 2200MHz
P1 = 1100MHz
P2 = 550MHz

So once again, asking anyone knows what to do, I do not like to run my GNU/Linux distro this hot !

**EDIT **- I might have forgotten to tell. I am undervolting under Windows !
The tool is called K10STAT.

---

### Post by Vaphell on 2009-10-16
if you add cpu freq monitor to the panel, does it show frequency go down when idle?

---

### Post by Turk4n on 2009-10-16
> **Vaphell said:**
> if you add cpu freq monitor to the panel, does it show frequency go down when idle?

Yeah, idle is P2 which is 550MHz...

---

### Post by ibuclaw on 2009-10-16
On a laptop there are generally three things that add to heat.

[LIST=1]
[*]CPU
[*]Hard Drive
[*]Graphics Card
[/LIST]

In reverse order, ways you can help prevent heat/watt/volt usage are by the following tricks:

Put the following coded lines in **/etc/rc.local** file
[LIST=1]
[*][COLOR="Sienna"]**Graphics Card**[/COLOR]
```
echo "powersave" > /sys/module/pcie_aspm/parameters/policy
```
This will set the PCI-E controller to powersave, other options available are "performance" and "default",

[*][COLOR="Sienna"]**Hard Drive**[/COLOR]
```
sudo hdparm -B 255 -S 12 -M 128 /dev/sda
```
This will set the hard drive to go into standby (spin down) after 1 minute of idleness. If this is too short, you can up the value of the -S switch to "24" to make it 2 minutes.

[*][COLOR="Sienna"]**CPU**[/COLOR]
We had a thread: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)
But that has since become a bit deprecated, as cpufreq is now compiled as part of the kernel, and not as a module. But you can still do the same thing, there is just a slightly different method of getting there, as should be available on the phc forum.
[/LIST]

Regards
Iain

---

### Post by Turk4n on 2009-10-17
> **tinivole said:**
> On a laptop there are generally three things that add to heat.

[LIST=1]
[*]CPU
[*]Hard Drive
[*]Graphics Card
[/LIST]

In reverse order, ways you can help prevent heat/watt/volt usage are by the following tricks:

Put the following coded lines in **/etc/rc.local** file
[LIST=1]
[*][COLOR="Sienna"]**Graphics Card**[/COLOR]
```
echo "powersave" > /sys/module/pcie_aspm/parameters/policy
```
This will set the PCI-E controller to powersave, other options available are "performance" and "default",

[*][COLOR="Sienna"]**Hard Drive**[/COLOR]
```
sudo hdparm -B 255 -S 12 -M 128 /dev/sda
```
This will set the hard drive to go into standby (spin down) after 1 minute of idleness. If this is too short, you can up the value of the -S switch to "24" to make it 2 minutes.

[*][COLOR="Sienna"]**CPU**[/COLOR]
We had a thread: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)
But that has since become a bit deprecated, as cpufreq is now compiled as part of the kernel, and not as a module. But you can still do the same thing, there is just a slightly different method of getting there, as should be available on the phc forum.
[/LIST]

Regards
Iain
The two first parts went flawless.
However the third one seemed not to go as good as the first 2. Uhm the values I changed and done, seem to be still there. Which makes me kinda sadden, I will try to fix this just wondering any application layered way to configure inputvoltage for CPU?

---

### Post by P4man on 2009-10-17
Windows isn't "undervolting" your cpu (beyond the values set by cool&quiet), so you shouldn't have to do that with ubuntu either.

A few things come to mind: 
1) are your fans actually running when in linux? Such a hugely high iddle temp when running at just 550 MHz makes me think the fan is not running at all.

2) Can you check your manufacturer website for a BIOS update? I saw someone else post a while ago with a Turion with similar problems, and he solved it with a bios update (which contained a microcode update for the CPU).

---

### Post by Turk4n on 2009-10-17
> **P4man said:**
> Windows isn't "undervolting" your cpu (beyond the values set by cool&quiet), so you shouldn't have to do that with ubuntu either.

A few things come to mind: 
1) are your fans actually running when in linux? Such a hugely high iddle temp when running at just 550 MHz makes me think the fan is not running at all.

2) Can you check your manufacturer website for a BIOS update? I saw someone else post a while ago with a Turion with similar problems, and he solved it with a bios update (which contained a microcode update for the CPU).

I might have forgotten to tell :P
I am undervolting in Windows... so just wanting to do the same with GNU/Linux...

---

### Post by HavocXphere on 2009-10-17
Forget undervolting there is something seriously wrong there.:shock:

At ~70C the CPU starts getting gradual but permanent thermal damage (this will take a while though).

Get the heatsink and thermal paste checked out on that thing ASAP....ideally by someone else than the person who did the original job.

---

### Post by P4man on 2009-10-17
> **HavocXphere said:**
> Forget undervolting there is something seriously wrong there.:shock:

At ~70C the CPU starts getting gradual but permanent thermal damage (this will take a while though).

Get the heatsink and thermal paste checked out on that thing ASAP....ideally by someone else than the person who did the original job.

Its a laptop. I agree those temps are too high to be normal (I still suspect a fan failure), but mobile cpu's shouldn't be damaged at 70°C. Like GPU's they can withstand higher temps. But the fact the laptop actually shuts down when stressed, should be a clear sign something is (very) wrong.

---

### Post by Turk4n on 2009-10-17
> **HavocXphere said:**
> Forget undervolting there is something seriously wrong there.:shock:

At ~70C the CPU starts getting gradual but permanent thermal damage (this will take a while though).

Get the heatsink and thermal paste checked out on that thing ASAP....ideally by someone else than the person who did the original job.

The laptop is only 2 months old. Also I have no dust currently inside have cleaned it one week ago...
SO nothing wrong...
Plus, there is no workstation that uses a Turion CPU. Also you see the temps I viewed, under windows it doesn't go overrated...I want the temps under Ubuntu to be better or identical with the ones in Windows...
Hopefully I will get this or something...

---

### Post by P4man on 2009-10-17
> **Turk4n said:**
> The laptop is only 2 months old. Also I have no dust currently inside have cleaned it one week ago...
SO nothing wrong...

Your laptop shuts down during normal operation, so something IS wrong. 

> Plus, there is no workstation that uses a Turion CPU. 

Of course not. Its a mobile CPU. Its designed to be low power and cool, attributes not so important in a large workstation.

> Also you see the temps I viewed, under windows it doesn't go overrated...I want the temps under Ubuntu to be better or identical with the ones in Windows...
Hopefully I will get this or something...


But you're undervolting it in windows. What are the temps like using stock settings? And once more, please confirm the fans are working under linux at all. Ive seen several cases of laptops with broken ACPI implementation where the fans didn't run at all under linux or didn't vary their speed. You could try adding 

```
acpi_osi="Linux"
```

to your kernel parameters.

---

### Post by Turk4n on 2009-10-17
> **P4man said:**
> Your laptop shuts down during normal operation, so something IS wrong. 



Of course not. Its a mobile CPU. Its designed to be low power and cool, attributes not so important in a large workstation.



But you're undervolting it in windows. What are the temps like using stock settings? And once more, please confirm the fans are working under linux at all. Ive seen several cases of laptops with broken ACPI implementation where the fans didn't run at all under linux or didn't vary their speed. You could try adding 

```
acpi_osi="Linux"
```

to your kernel parameters.

My computer haven't been shut down once by heat.
Also, stock temps Under Windows without undervolting is the same as in GNU/Linux now. So that's why am asking a method to undervolt in GNU/Linux systems for newer turions. Plus my fans runs, idle runs midly. Running loud only when reaching full load in GNU/Linux, which means when running Ubuntu and doing things at full load, the fans sounds as under Windows 7 while gaming..(Note I have undervolted...under Windows however not in Ubuntu...)
Hope this was enough info...

---

### Post by P4man on 2009-10-17
earlier you said "gaming will result the laptop shuts off". I guess I misread?

Anyway, on a new laptop you shouldn't be "hacking" with undervolting just to get it working properly. Id try a bios update, or send it back. But to answer your question: I got no idea Im afraid.

---

### Post by Turk4n on 2009-10-17
> **P4man said:**
> earlier you said "gaming will result the laptop shuts off". I guess I misread?

Anyway, on a new laptop you shouldn't be "hacking" with undervolting just to get it working properly. Id try a bios update, or send it back. But to answer your question: I got no idea Im afraid.

No you didn't misread, it was I that was unclear, without undervolt, and gaming resulting it to shut off. With Undervolt and gaming no problem running games and etc.
I have always had this knowlegde and knew before that the Turions are bad in terms of producing large amounts of heat. However the price and performance it gave. Made me buy it...Now I regret since I can't run GNU/Linux properly !
I still have a lot of thoughts of getting another laptop...
Or just keep this and find a solution :confused:

---

### Post by P4man on 2009-10-18
> **Turk4n said:**
> No you didn't misread, it was I that was unclear, without undervolt, and gaming resulting it to shut off. With Undervolt and gaming no problem running games and etc.
I have always had this knowlegde and knew before that the Turions are bad in terms of producing large amounts of heat. However the price and performance it gave. Made me buy it...Now I regret since I can't run GNU/Linux properly !
I still have a lot of thoughts of getting another laptop...
Or just keep this and find a solution :confused:

Turions may not be the coolest mobile cpu's on earth, but laptops built around them should still not shut down running normal software like games.  Especially not for a laptop branded as "Entertainment Notebook PC". RMA it. It probably has faulty heatsink assembly.

---

### Post by Turk4n on 2009-10-18
> **P4man said:**
> Turions may not be the coolest mobile cpu's on earth, but laptops built around them should still not shut down running normal software like games.  Especially not for a laptop branded as "Entertainment Notebook PC". RMA it. It probably has faulty heatsink assembly.

I will do, if no solution is present. I have still 10 months left of my warranty :>

---

