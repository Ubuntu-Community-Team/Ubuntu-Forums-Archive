---
title: "Horrid Battery Life"
date: 2006-06-05
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-05
Hey all, apparently Ubuntu hasent mastered battery power... I get one hour less battery power then I did on windows at lowest screen brightness. lowest brightness on each OS, I get 3 hours on windows, 2 on Linux. almost less then 2 actually.

is there anything I can do?

---

### Post by garyng on 2006-06-05
use XP. This is not just an ubuntu issue but linux in general.

---

### Post by Patrick-Ruff on 2006-06-05
that is not a useful answer in the slightest, you remind me of a mac  user...and mac users are a**holes. that may be a stereotype, but its a pretty accurate one. now, give me a real answer because going back to XP is obviously not an option for me.

---

### Post by cleentrax on 2006-06-05
Are you basing battery life on the monitor, or on actual loss of power? I have noticed that Gnome's battery monitor is not as accurate as Windows'.

Do you have a "stepping" processor? Is it properly scaling to the workload? You can find out by R-click Panel -> Add to Panel -> System & Hardware -> CPU  Frequency Scaling Monitor.

---

### Post by Patrick-Ruff on 2006-06-05
it seems like it is. but sometimes it scales it down to 400 mhz, but its only going as low as 800. either way, CPU scaling is owrking it seems.

---

### Post by garyng on 2006-06-05
[QUOTE=Patrick-Ruff]that is not a useful answer in the slightest, you remind me of a mac  user...and mac users are a**holes. that may be a stereotype, but its a pretty accurate one. now, give me a real answer because going back to XP is obviously not an option for me.[/QUOTE]

good luck then. As for stereotype, I am not sure what it means. I have 7 or so linux + 3 XP, each chosen because of different reasons and power management + wireless is the top two reasons why I would not run linux for machines that need them.

---

### Post by Patrick-Ruff on 2006-06-05
I see. well there must be some way to pump more juice out of that battery, I'de rather not buy a 9cell.

---

### Post by karthik085 on 2006-06-05
try PowerNowd for adjusting the speed of your CPU

---

### Post by Patrick-Ruff on 2006-06-05
PowerNowd? whats that?

---

### Post by nocloud on 2006-06-06
also you can try disabling the network card when ur not using it

another viable option is reducing the speed of ur graphics card by activating a feature like powerplay

---

### Post by David Corrales on 2006-06-06
I have to agree. I lose 1.5 hours in linux. It's just the way things are implemented:
- x.org is buggy so it eats more cpu on my Inspiron 9300.
- The automatic video power consumption reduction for video cards isn't there
- Options like turning off the internal network card don't appear anywhere

For my laptop, I have to use a 386 kernel because the 686 is buggy and it's 90% cpu on idle lol. Isn't there a project or something planning to make it at least as good as Windows? I'd be really interested in something like that.

---

### Post by nocloud on 2006-06-06
- The automatic video power consumption reduction for video cards isn't there

for ati cards, you need to install the fglrx driver and then use the following commands:
aticonfig --list-powerstates
Set your power-state:
aticonfig --set-powerstate=NUMBER

- Options like turning off the internal network card don't appear anywhere

you can find that option under system settings --> network settings

---

### Post by Patrick-Ruff on 2006-06-06
oh well I suppose I'll just deal with the problem for now.

---

### Post by Seq on 2006-06-06
[QUOTE=nocloud]- The automatic video power consumption reduction for video cards isn't there

for ati cards, you need to install the fglrx driver and then use the following commands:
aticonfig --list-powerstates
Set your power-state:
aticonfig --set-powerstate=NUMBER

- Options like turning off the internal network card don't appear anywhere

you can find that option under system settings --> network settings[/QUOTE]For using the regular radeon dri driver (from memory, I may be slightly incorrect):
```
Option "dynamicClocks" "true"
```

ensuring laptop-mode is enabled is also important. Also, you can tweak the rules powernowd uses to scale the cpu. The default is to jump to full cpu frequency when utilization (at the reduced frequency) goes over 80%, then slowly step back down. You can change this to the reverse (slowly step up, then drop down when not needed). 

Find programs that do lots of disk access (firefox caching, gaim logging, etc), and try to minimize this (disable gaim's logging, maybe turn off caching in firefox, though this would cause other issues). laptopmode in the kernel attempts to buffer writes to minimize spinups, but data reads are also an issue. Low memory systems may swap as well, which would cause disk useage.

I have two notebooks currently: 
- a gateway 450X (450rog) "centrino" notebook, which now gets ~40 minutes in both windows and dapper. It used to get roughly 3 hours for windows, and 2.5 for whatever Linux distro I happened to use at the time
- Apple iBook G4, which gets 3.5+ hours in OSX or Ubuntu, with minimal "tweaking" (never worried about application disk access much).

I am far from an expert on these matters, but I have seen battery life all over the place. In my opinion (note "opinion": not of any real technical merit), it is not so much that Linux can not allow long battery life, but I would rather think some laptops are not properly supported -- maybe due to fun ACPI stuff or something. I don't know what to "blame", but I know that linux is perfectly capable of good battery life on some hardware, and exceptional on others.

---

### Post by shuttleworthwannabe on 2006-06-06
On e issue is xorg on a linux-686 kernel. Try moving to linux-386. On my system the battery life was lsightly better on 386, but not as much as XP. I get full 4 hours on XP, only 1:30 on Ubuntu.

It is indeed a pity that we have such a powerful and user friendly OS and yet such basics are overlooked?

I have brought this issue up during the Dapper develp period, but I did not see a propoer solution to this. Launchpad has the -686 bug listed, but there is not further progress on it either.

Just bear with it for some time. Seq and nocloud suggestions are refreshing, and i am tempted to try them out.

Thanks

---

### Post by compmodder26 on 2006-06-07
I had terrible battery life too before I discovered that the wirless card was the major culprit.  I found that "iwpriv" was useful for my situation.  I have an Intel 3945ABG PCIE card.  I can't guarantee that it will work for you.  Here is a tutorial on how to use iwpriv to control the Power Saving Protocol feature in the intel 3945ABG card: [http://ipw3945.sourceforge.net/README.ipw3945](http://ipw3945.sourceforge.net/README.ipw3945) (you'll have to scroll down to section 3.9, no anchors).  Like I said, this is for the Intel card so if you don't have that then these instructions may not work for your particular card.

---

### Post by meridius on 2006-06-07
Linux can use different power management profiles called "governors." By default, Ubuntu does not allow you to change which governor it uses, however you can enable the option with one command:

$ sudo dpkg-reconfigure gnome-applets

After that, make sure you have the "CPU Frequency Monitor" applet running in your Gnome panel. Right click on the applet and go to the Preferences. Under "Frequency Selector" section, make sure the "Show menu" is selected on "Frequencies and Governors."

Then you can left click on the applet and from here, choose which governors or frequencies to use.

If you're confused as to which governor to use, just try them all. There shouldn't be too many.

---

### Post by David Corrales on 2006-06-07
[QUOTE=nocloud]- The automatic video power consumption reduction for video cards isn't there

for ati cards, you need to install the fglrx driver and then use the following commands:
aticonfig --list-powerstates
Set your power-state:
aticonfig --set-powerstate=NUMBER

- Options like turning off the internal network card don't appear anywhere

you can find that option under system settings --> network settings[/QUOTE]

Hmmm interesting find on the video power thing, anyway to automate this?

The problem with the network card is you can disable it, but it probably still consumes power.

---

### Post by David Corrales on 2006-06-07
I just set my video card power mode to 1 and it does indeed help quite a bit. Like 30-40 minutes and for a regular desktop it all looks the same...

---

### Post by compmodder26 on 2006-06-07
[QUOTE=meridius]Linux can use different power management profiles called "governors." By default, Ubuntu does not allow you to change which governor it uses, ...[/QUOTE]

You can change this via the command line without having to enable anything.  Just go to /sys/devices/system/cpu/cpu0/cpufreq/ (if you have multiple processors/cores/hyperthreading change cpu0 to cpu1, cpu2, etc. for each cpu you have listed) and edit the file (use sudo) "scaling_governor", just change the governor that is listed to whatever governor you want to use. Available governors are listed in "scaling_avail_governors"

---

### Post by The Darkness on 2006-06-07
Very nice find on the video power scaling.
My Inspiron XPS has horrid battery life to begin with.
I drained it to nothing in less than 5 minutes from full charge the other day, once I pulled the plug.

---

### Post by vseehua on 2006-06-07
cool... with the govenor set to powersave, even my laptop's fan spins up less frequently now...thanks... ;)

---

### Post by xoui on 2006-06-07
In my case it is the GPU that consumes the power because my CPU frequency is scaled and still I get less battery life. It seems that nVidia driver doesn't support power management. Does anyone know how to turn on the scaling of nVidia GPUs?

---

### Post by meridius on 2006-06-08
[QUOTE=compmodder26]You can change this via the command line without having to enable anything.  Just go to /sys/devices/system/cpu/cpu0/cpufreq/ (if you have multiple processors/cores/hyperthreading change cpu0 to cpu1, cpu2, etc. for each cpu you have listed) and edit the file (use sudo) "scaling_governor", just change the governor that is listed to whatever governor you want to use. Available governors are listed in "scaling_avail_governors"[/QUOTE]

When I said, "By default, Ubuntu does not allow you to change which governor it uses," I meant that Ubuntu doesn't allow you to change the frequencies or governors via the CPU Frequency Monitor applet by default.

I also think you missed the whole point of my post. By enabling the option, you have a quick way of changing governors in the CPU Frequency Monitor instead of having to go into /sys/devices/system/cpu/cpu0/cpufreq/ then modify the scaling_governor file of each cpu everytime you wish to change governors.

As an example, when my laptop is using the battery, I choose the powersave governor. When my laptop is plugged in, I choose the performance governor. I would go crazy manually editing the governor files each time. Furthermore, when I tried manually changing the values of scaling_governor, it didn't allow me to modify the file (yes, I was using sudo).

---

### Post by compmodder26 on 2006-06-08
I didn't miss the point.  I was simply stating that you don't have to download any extra packages to get it to work.  Sorry if I made seem like I was contradicting you. 

As for not allowing you to modify it, I can't help with that.  I can modify mine just fine.

I've created some simple scripts that you can place into the battery.d and ac.d folders in /etc/acpi that will do the switching for you.

As root, create a file (name it what you want) and place it in **ac.d** with this in it:
```
#!/bin/sh
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

As root, create a file (name it what you want) and place it in **battery.d** with this in it:
```
#!/bin/sh
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

**EDIT: Don't forget to make the files executable.  Also just realized that I forgot to mention that the scripts should have a .sh extension, otherwise they won't be called.**

Of course you can change the governor to what you want in each script and again if you have multiple cpus/cores/hyperthreading, you can add the same lines in each script and just replace cpu0 with cpuX where X is the number of the other recognized cpu(s).

---

