---
title: "CPU Frequency Scaling Monitor Doesn't Work!"
date: 2011-06-01
forum: General Help
---

### Post by gnome1919 on 2011-06-01
Hi buddies,
I have recently installed Ubuntu 11.04 on my PC with these configuration:

CPU: AMD Athlon 7750 Black Edition
RAM: 2GB 1066 MHz
VGA: ATI Radeon HD 3200 (on AMD 780G)

After I installed Natty Narwhal I felt that my CPU runs at the highest clock all the time (2.7GHz), even if I don't have any program run. I tried all settings for AMD Cool'n'Quiet from mainboard BIOS, but nothing's changed. I installed "CPU Frequency Scaling Monitor" to manually change CPU clock. It recognizes two clock for my CPU, 2.7GHz and 1.35Ghz plus 4 other options; Conservative, Ondemand, Performance and Powersave but the CPU indicator doesn't change on every option! The CPU fan noise makes me crazy, any help would be appreciated.

Thanks in Advance

---

### Post by johngreth on 2011-06-01
Does the frequency change at all, or is it just not changing when you expect it to?

---

### Post by gnome1919 on 2011-06-01
Thanks for your reply johngreth;

No, there is no change at all on CPU meter. it shows 100% or 2.7GHz (Maximum) on every options!

---

### Post by johngreth on 2011-06-01
It should work when Cool'n'Quiet is enabled in the bios. Maybe the bios needs to be updated?

---

### Post by gnome1919 on 2011-06-01
I already tried all Cool'n'Quiet options in BIOS; AUTO, ENABLED and DISABLED but to no avail!

---

### Post by pqwoerituytrueiwoq on 2011-06-01
try installing powernowd
[FONT=Courier New]sudo apt-get install powernowd[/FONT]
make a through search through your biso options
as far as i know Cool'n'Quiet only effects fan speed not core speed

---

### Post by gnome1919 on 2011-06-02
Thanks for your reply pqwoerituytrueiwoq,
about your second comment; CPU fan speed is not controllable separately from CPU core speed. In fact CPU fan speed decreases when CPU core clock decreases as well.
 
It seems that I should quit "CPU Frequency Scaling Monitor" first to make powernowd to work. I did it and again nothing happened! powernowd tells me that I have two supported steps in my CPU (1.35 and 2.7 Ghz), I tried "sudo powernowd -m 1" (Aggressive Mode) and "sudo powernowd -q" (Quiet Mode) but all to no avail! The first command returns:

[I]powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
powernowd: Found 2 scalable units:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 1350Mhz - 2700Mhz (2 steps)
powernowd:   cpu1: 1350Mhz - 2700Mhz (2 steps)[/I]

and the second one (quiet mode) returns nothing!

any idea?

---

### Post by bazcor on 2011-06-02
Try installing cpufrequtils, it worked for me.

good luck .. Barry

---

### Post by gnome1919 on 2011-06-02
> **bazcor said:**
> Try installing cpufrequtils, it worked for me.

good luck .. Barry

Thank you very much Barry, It worked!
I have another question; I want to add other frequencies in "CPU Frequency Scaling Monitor" option (I have Max=2.7GHz and Min=1.35Ghz already). How can I find which frequencies my CPU supports to work safe and stable?
Also I think that I should edit available frequencies in "scaling_available_frequencies" file exist in "/sys/devices/system/cpu/cpu0/cpufreq" folder, am I right?

Thanks in Advance.

---

### Post by bazcor on 2011-06-02
Edit: For relevance.

I don't think you can add extra frequencies, it's all down to the capabilities of your cpu. Mine has four available frequencies, the CPU I ran before (An Intel q6600) only had two!

Check the spec' of your chip and see what it is capable of.

..Barry

---

### Post by gnome1919 on 2011-06-02
New problem!
I found that on each reboot the value of the file "scaling_min_freq" reset to the value of the file "scaling_max_freq" (mine is 2700000KHz), and I should change it manually after each reboot through Terminal so i can reach lower frequency (which is 1350000KHz)! How can I solve this problem?!

---

### Post by gnome1919 on 2011-06-02
no idea?

---

### Post by pqwoerituytrueiwoq on 2011-06-02
add the command to startup applications that sets it *(post the command here while you are at it for others with this issue)*
if it is a sudo command i think you can get it by adding a desktop file in [FONT=Courier New]/usr/share/gdm/autostart/[/FONT]
if that does not work
[FONT=Courier New]gksu gedit /etc/gdm/Init/Default[/FONT]
Add the command line right before exit 0 at the end of the file
edit: BTW i think the cool n quiet feature controls the fans based on the temperature not the core speed 
for example if i set my CPU to run at 100% speed (aka performance mode) the fan speed does not budge
*(using a _amd phenom ii x4 965 black edition_ cool n quiet is enabled)*

---

### Post by gnome1919 on 2011-06-05
> **pqwoerituytrueiwoq said:**
> add the command to startup applications that sets it *(post the command here while you are at it for others with this issue)*
if it is a sudo command i think you can get it by adding a desktop file in [FONT=Courier New]/usr/share/gdm/autostart/[/FONT]
if that does not work
[FONT=Courier New]gksu gedit /etc/gdm/Init/Default[/FONT]
Add the command line right before exit 0 at the end of the file
edit: BTW i think the cool n quiet feature controls the fans based on the temperature not the core speed 
for example if i set my CPU to run at 100% speed (aka performance mode) the fan speed does not budge
*(using a _amd phenom ii x4 965 black edition_ cool n quiet is enabled)*

Thanks for your reply,
I try to describe my problem to clarify what I need to do exactly;
Problem: I finally found it. The problem is that the value saved in the file "scaling_min_freq" is set to the value of the file "scaling_max_freq" which both are 2.7GHz. When I changed first file value to 1.35Ghz the problem solved, but each time that I reboot the system the value of the file resets to 2.7GHz again! the command line that I use to change the file value is something like this:
"sudo gedit /sys/device/system/cpufreq/cpu0/scaling_min_freq"
Then change the value manually in text editor and then save it.

What I want to do: do this automatically at each restart. I'm a new user to Linux, and don't know, maybe it's a better way like locking the file to prevent it from changing at each startup. 

Please help me :(

P.S: About Cool'n'Quiet feature; I don't think that you can control fan speed or better to say the noise directly! Because CPU fan is dependent to CPU load or the core clock that CPU runs at (which makes the CPU temp go up and then fan speed as well). I have Windows 7 on this machine too (Dual Boot), when I want to reduce the CPU fan speed or the noise, I simply run a software which comes with mainboard (MSI Dual-Core Center) and choose the option "Silence", which suddenly makes the core clock drop to 1.2 to 1.3 GHz and after 10 to 15 seconds the CPU fan speed or the noise is reduced consequently. ;)

---

### Post by Rebelli0us on 2011-06-05
CPU Frequency Scaling Monitor is just to display frequency, it doesn't control cpu freq or voltage.

---

### Post by gnome1919 on 2011-06-06
Please!
bump, bump...

---

### Post by miscreanity on 2011-07-02
If you have cpufreqd installed, try removing it.

```
sudo apt-get remove cpufreqd
```

Stick with cpufreq-selector or the tools from cpufrequtils for command-line management.

---

### Post by gnome1919 on 2011-07-06
> **miscreanity said:**
> If you have cpufreqd installed, try removing it.

```
sudo apt-get remove cpufreqd
```

Stick with cpufreq-selector or the tools from cpufrequtils for command-line management.

Thanks a lot miscreanity,
It worked. Removing "cpufreqd" and installing "cpufrequtils" as you said.
Thanks again.

---

