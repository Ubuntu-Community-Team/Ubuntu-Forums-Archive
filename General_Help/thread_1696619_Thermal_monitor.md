---
title: "Thermal monitor"
date: 2011-02-27
forum: General Help
---

### Post by alextulu on 2011-02-27
I dindn't get to install Ubuntu yet because of a problem. I need to activate thermal monitor because my laptop overheats, but my BIOS doesn't have any options for thermal monitor and the only way I can enable it is by using RightMark CPU Clock wich only runs in Windows. If I don't enable it, my laptop shuts down when I play a game (it only activates for very short periods and doesn't affect the game performance very much). This is why I'm asking if thermal monitor can be enabled from Ubuntu or maybe if RightMark can run in Wine (although I don't think it can).I know I should do something about the cooling system, but even if I do, considering my laptop is a Acer, you never know when the cooling might fail again.

---

### Post by Frogs Hair on 2011-02-27
Hi and Welcome

```
sudo apt-get install lm-sensors
``` and to view CPU temp. run ```
sensors
``` in the terminal

---

### Post by alextulu on 2011-02-27
Does lm-sensors only enable me to view temperatures or does it also enable thermal monitor ?

---

### Post by Frogs Hair on 2011-02-27
After you install lm-sensors , at least on the desktop edition , You could install sensors-applet and right click your panel and add it to the panel to display hardware temps.

It has a a couple of display options in the preference settings , but it is only a display and controls nothing.

---

### Post by alextulu on 2011-02-27
I read the following post on the RightMark forum:

"Does anyone know of a similar program or linux version of this program that I can run in linux (ubuntu more specifically)?

Unfortunately, there's no Linux version of RMClock.
However, there seem to be some Linux kernel modules providing the way of managing CPU performance/power management."

Can anyone tell me what those modules are ?

---

### Post by cchhrriiss121212 on 2011-02-27
You are talking about 2 separate things here:
A thermal monitor will tell you what temperature your CPU is but it won't solve your overheating issue
A frequency scaling app (like RMClock) will change the speed of your CPU, which causes it to draw less power and thereby runs cooler

To achieve the latter: Right click the top panel and add an applet, in the list you should see an option for CPU frequency scaling. Select this and set it to whatever level you need to keep the heat down.

---

### Post by alextulu on 2011-02-28
I'm not talking about a thermal monitoring application, I'm talking about the thermal monitor 1&2 in Intel CPU's. When the CPU reacheas about 2 degrees celsius below maximum temperature, thermal monitor inserts HALT instuctions and also decreases the frequency by half wich cools the CPU. Normally that option is found in the BIOS, but my Acer laptop doesn't have that option in it's BIOS and the only way i can activate it is by using RightMark wich doesn't have a linux version.

---

### Post by cchhrriiss121212 on 2011-02-28
OK I see what you mean. In any case the solution I posted is still applicable. You could set up a script to throttle at certain temps, or just keep an eye on how hot it is and change when you need to.

But if your laptop is regularly reaching maximum temps, I would have it looked at, otherwise it won't last very long.

---

### Post by alextulu on 2011-02-28
In that case please tell me how to make that script.

---

### Post by cchhrriiss121212 on 2011-02-28
I can show you the basics, but you will have to look up the specifics yourself. Here is what I would do:
First install lm-sensors and check your temps, using the method frogs hair explained
Check [this guide]("http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/") for how to use cpufreq (which is already installed)
Open gedit and write want you want done:
```
#! /bin/bash
if your commands...
```
Save it with an sh extension and allow it to run as a program under properties tab
Add the script to your autostart menu

If you don't want to get into all that, just use the applet and set it at half speed permanently. This is probably better for your CPU anyway.

---

### Post by psusi on 2011-02-28
The word monitor means to look at, so when you ask for a thermal monitor, you are only asking for something that reads the temperature.  The process you describe to try and limit the temperature is called throttling.  It is the last ditch effort to prevent overheating, and is supposed to be done automatically by the bios.  If the system is properly designed, it should not even be needed since when the fan is running at full speed, it should not overheat under full load.  You should make sure that your fan is working, and not clogged with dust.  Aside from that, use the frequency scaling applet to limit the processor speed, which is better than throttling.

---

### Post by cloyd on 2011-02-28
THis was the solution for fan control problems on my Gateway netbook. Don't know that it will work for you, but it may be worth a try. Some temp and fan control issues are machine specific.
 
Use acerhdf.

So that the acerhdf module runs at boot time

sudo gedit /etc/modprobe.d/acerhdf.conf  and insert the following

options acerhdf interval=5 fanon=58000 fanoff=53000 kernelmode=1

I the file doesn't already exist, this will create it. This assumes that acerhdf is on your system. I do believe I had to install it on mine.

If your machine supports acerhdf, this turns the fan on at 58 C and off when it gets down to 53. The interval between them is 5 degrees. Don't know why it is 58000 instead of 58, but that is how it works. You may want to try other values, but I have heard that best results are obtained when the interval between values is 5. 

Don't know that it will work, but it improved how my machine runs.

---

### Post by alextulu on 2011-03-01
I searched about how Intel thermal monitor is activated and I found that i need to modify a model-specific register (MSR) called IA32_MISC_ENABLE. Can someone tell me how to use a MSR editor ?

---

