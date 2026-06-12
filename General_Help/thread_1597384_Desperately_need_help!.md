---
title: "Desperately need help!"
date: 2010-10-15
forum: General Help
---

### Post by ginnie6 on 2010-10-15
I'm on Lucid on an HP laptop...DV 9500. The lockups are driving me crazy! I've never experienced this many issues with ubuntu before this. I can't leave my computer on for longer than 12 hours. Window decorations disappear and then the keyboard stops working. Can't shut down, switch desktops or anything. The only thing I can do is a hard shut down....then its okay for awhile. Its past the point of being an aggravation.....I lost a whole blog post just now. Does anyone have any ideas what is causing this?

---

### Post by matt_symes on 2010-10-15
Hi,

Are you sure its not a hardware problem.(cpu overheating, harddrive in failure,  fan on the blink). Most of the times i have had issues like this it has been hardware related.

When did it start happening. After you _installed_ or _upgraded_ to lucid ? how long afters?

Have you checked in the logs at /var or system->administration->log file viewer. 

This might give you an indication of what is going on.
Need more info as a starting point.

Kind regards.

---

### Post by dallasWolf on 2010-10-15
There is a least two possible things that can be causing this. The processor may be getting too hot exceeding the normal operating parameters after running for sometime. Another possibility and much worse scenario is that your hard disc maybe heading for a crash.

---

### Post by ginnie6 on 2010-10-15
I don't think its hardware failure....it just started when I did a clean install of lucid. Before with jaunty no issues. I'm not sure what to look at in the log.

---

### Post by 3Miro on 2010-10-15
Check your CPU usage to make sure there are no rogue processes taking 100% of one core and making the ocmputer overheat.

While checking the CPU, check the RAM uage as well, sometimes a process may leak memory draining resources from your system over time.

A friend of mine used to have a nice 3D screensaver, however, the computer had hard time handling all the effects and would often overheat. Change the screensaver to "blank screen" to see if this helps.

Turn the visual effects from "Normal" to none, to see if this helps. If so, you can turn them back to normal and possibly lower some of the settings (install ccsm).

Disapearing window decorations make me think that the visual effects may be the reason for he problem, but check the other options as well.

---

### Post by matt_symes on 2010-10-15
Hi,

It could very well not be a hardware issue, but there are some tests you can

Hard disk check    

1.  sudo touch /forcefsck
2.  restart ubuntu to run disk check. This will check the integrity of the file system but not the drive itself

Memory check    

1. [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

Temperature.  Below is a tutorial on how to use sensors

[http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/](http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/)

This check is more complicated. You can use smartctl to check the drive using SMART if it has it. Below is a tutorial.

[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

They will take a bit of time but will help to eliminate some issues, as these have been  the main hardware issues that have bitten me in the past. If it is a software issue then these test are still useful to know.

Kind regards

---

### Post by matt_symes on 2010-10-15
Hi,

Read this as well

[http://ubuntuguide.net/how-to-reboot-a-frozen-ubuntu-the-safe-way](http://ubuntuguide.net/how-to-reboot-a-frozen-ubuntu-the-safe-way)

It a fail safe way to shutdown ubuntu in the event of a system freeze, so you dont just have to turn the power off. 

If it does not work, the issue is serious.

Kind regards

---

### Post by matt_symes on 2010-10-15
Hi,

There are a number of software issues it could be. 3Miro is correct to check the CPU and memory usage. 

Open a terminal and use top or htop. (sudo apt-get install htop) and look for any processes that are hogging the CPU or memory around the time of a crash. Watch this carefully and get a screen shot or photo if you can before you reboot  These could be causing the problem. 

Make a note of all the applications you have open and see if there is a pattern of open applications and investigate their status at the time of a crash.

Check you hard disk at this time and see if it is being thrashed. It could be your memory if full and you are using all your swap space. I've seen stranger things, but usually on a well known legacy operating system.

If your entire system is freezing i would say its more lightly to be a kernel or kernel module, but you never know. My post above will identify this.

Kind regards

---

### Post by matt_symes on 2010-10-15
Hi,

Another thing it may be is X freezing.

Here is ubuntu's tutorial

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Kind regards

---

### Post by matt_symes on 2010-10-15
Hi,

Take particular note of the system and non symptoms of an X freeze.

**Symptoms** 

[LIST]
[*]X stops responding to input (sometimes mouse cursor can still move, but clicking has no effect) 
[*]The screen displays but does not update.  Sometimes there is screen corruption too, but usually there isn't. 
[*]Often, X cannot be killed; only a reboot clears the state 
[*]The system operates fine over SSH but not on the graphical console 
[*]It can be hard to tie the problem to an exact test case; it seems to occur "randomly" 
[/LIST]
**Non-Symptoms** 

[LIST]
[*]A backtrace appears in Xorg.0.log or elsewhere - most of the time this indicates a crash, not a freeze 
[*]Screen blanks to a solid color (See [X/Troubleshooting/BlankScreen]("https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen") instead) 
[*]The caps lock key blinks - this indicates a kernel failure, not X 
[*]CPU load is high.  This indicates a performance issue rather than a freeze 
[*]Screen still updates (look at clock), but can't be interacted with - probably is an input bug, not a GPU freeze 
[*]System freezes for a period but then comes back.  Real freezes never come back.
[/LIST]
Keep an eye out for the non symptoms as well. 
All this info could very well be overkill, however it is always hard to identify issues like my machine crashes.

BTW have you tried reinstalling?
Or maybe that's too windows.....

Kind regards

---

### Post by coffee412 on 2010-10-15
> **ginnie6 said:**
> I'm on Lucid on an HP laptop...DV 9500. The lockups are driving me crazy! I've never experienced this many issues with ubuntu before this. I can't leave my computer on for longer than 12 hours. Window decorations disappear and then the keyboard stops working. Can't shut down, switch desktops or anything. The only thing I can do is a hard shut down....then its okay for awhile. Its past the point of being an aggravation.....I lost a whole blog post just now. Does anyone have any ideas what is causing this?

I just wanted to chime in here on one fact. HP Pavilion Laptops with the nvidia graphics are known to have problems with the graphics chipsets overheating and damaging the motherboard. Normally this happens about 1 year from purchase. HP has been in a few lawsuits about this and still some pending stuff going on. 

All I am saying is that this might not be a O/S problem at all. It very well could be your laptop failing after a while from heat issues. Wouldnt matter what operating system you used.

I have a few customers with similar laptops to yours and HP (when in warranty period) replaces them with the same exact motherboard that then burns out again. However, By then the warranty is over and you have a brick. 

JMHO from a Repair Technician

---

### Post by matt_symes on 2010-10-15
Hi,

Cheers coffee. Did not know about that over here in ye olde england.

Kind regards.

---

### Post by ginnie6 on 2010-10-15
thanks ya'll...its the hard drive. Went into System/ Admin/ Disk Utility and it shows the hard drive has some bad sectors. 
Looks like I'll be backing up a few things and ordering a new hard drive. Oh and I always use a cooling pad with the laptop to avoid overheating.

---

