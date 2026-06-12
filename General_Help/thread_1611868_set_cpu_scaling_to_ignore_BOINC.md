---
title: "set cpu scaling to ignore BOINC"
date: 2010-11-02
forum: General Help
---

### Post by michael_j_w on 2010-11-02
Hi,
 
I am trying to set up my cpu freq. scaling to ignore BOINC. From what google has shown me this is done by setting a value of 1 for ignore_nice_load. However the location of said value does not seem to be the same in 10.04 as in the results from google. 
 
How do i set this or is there a better way to keep idle processes like BOINC from increasing the my cpu frequency? 
 
Thanks!
 
Michael

---

### Post by TBABill on 2010-11-02
Are you actually noticing cycles jump up to higher settings with BOINC enabled? What if you kill it then do you see immediate CPU freq drops? Are you set to powersave or ondemand, or are you set to performance?
 
In a terminal you can type ```
cpufreq-set -help
``` and see if there is an option to set it to ignore a specific application's demand for higher CPU freq. I'm not home to try it out right now.

---

### Post by michael_j_w on 2010-11-02
Yes the frequency jumps up and down. Yes it stops when BOIC is killed or goes to sleep. Yes i have tried multiple power profiles. ondemand and conservative both cycle, powersave obviously does not but it is not my goal to lock the frequency, only prevent BOINC from causing an increase or preventing a decrease in it. 

BOINC has a nice value of 19 in top/htop. it is my goal to prevent any process with a nice value of 19 from causing an increase in proc freq, though preventing any process with a nice value would be just fine too. there are instructions for doing this on Jaunty all over google but the command specified points into a dir that does not exist in 10.04. What i need is either the updated location of the target file or a better/alternative method to accomplish the goal. 

[SOLVED]

either the commands i saw via google were wrong or i read them incorrectly but the path to the file on 10.04 is: 

/sys/devices/system/cpu/cpufreq/ondemand/ignore_nice_load 

Just change the 0 to a 1 and save. thats it. all is working properly now. Processor is running at 100% capacity and 50% frequency!

[SOLVED]


Michael

Not that it probably matter for this issue but here are system specs:
Intel E3300 2.5ghz
2gb ddr2
sata hdd drive
headless/onboard video
ubuntu 10.04.1 i686 generic kernel

---

### Post by TBABill on 2010-11-03
Michael, thanks for posting the final fix. Others may also want to use BOINC and this would be helpful for them.

---

### Post by dcstar on 2010-11-04
> **michael_j_w said:**
> 
..........
either the commands i saw via google were wrong or i read them incorrectly but the path to the file on 10.04 is: 

**/sys/**devices/system/cpu/cpufreq/ondemand/ignore_nice_load 

Just change the 0 to a 1 and save. thats it. all is working properly now. Processor is running at 100% capacity and 50% frequency!
.........

/sys is a dynamic system folder that is totally reset at every reboot, it is pointless making any change there that you want to remain after rebooting.

Install the **powernowd** package, the default will not use niced processes in the scaling.

---

### Post by dcstar on 2012-09-21
Updating this thread for 12.04:

If you want to have the default 12.04 CPU management ignore "nice" processes when deciding to up the CPU core clock then you need to do the following:

```
sudo gedit /etc/init.d/ondemand
```
Find the block of code that looks like this and inset the **bold** lines:
```
	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done
[B]	# Set CPU power management to ignore "Nice"d processes.
	 echo -n "1" > /sys/devices/system/cpu/cpufreq/ondemand/ignore_nice_load[/B]
	;;
```
That key defaults to 0 on boot up and I cannot find where to change that, but this will set it in a place that does not crash your system (I tried other places like /etc/rcS, don't do this!).

Running BOINC will now not ramp up your CPU to maximum clock rate even if your CPU is doing nothing else. The CPU rate will still change as normal when other processes put demands on your system.

This change may or may not survive updates and upgrades and may not be valid in future Ubuntu versions, so keep this in mind.

---

