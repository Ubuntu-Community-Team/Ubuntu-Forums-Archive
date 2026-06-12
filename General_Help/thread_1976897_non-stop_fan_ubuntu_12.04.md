---
title: "non-stop fan ubuntu 12.04"
date: 2012-05-09
forum: General Help
---

### Post by javi_m on 2012-05-09
Hi everyone.

I made a fresh install of ubuntu 12.04, and the fan is working all the time.

Also, the temp is a little bit higher compared with ubuntu 11.10.

Installed lm-sensors, and it indicates 55-60ºC. In ubuntu 11.10 it was 48-53ºC, jumping to 60-65ºC when using some heavy apps.

I'm not sure if the problem it's a high temp, or if the fan controller is not working quite well.

It is weird to have that temp variation, since 12.04 looks kinda similar to 11.10

Thanks in advance



PS: lm-sensors says: (high = +80ºC, crit = +85ºC), but this same laptop was cooler with ubuntu 11.10, that's the strange thing.

PS2: Laptop: Lenovo G570, Intel I3-2310M @ 2.10 Ghz

---

### Post by smurphy on 2012-05-09
Guess that nepomuk is running and indexing your files.
Let it finish the run. Should be better then (Nepomuk is under KUbuntu, dunno if they use something else for Ubuntu).

---

### Post by iMurshaq on 2012-05-09
Odd, is it possible that you dropped your computer if it is a laptop. If so, then you may have messed up your heatsink.

---

### Post by javi_m on 2012-05-09
@smurphy: Don' think that nepomuk it's indexing any file. Don't know either if nepomuk works (or it's equivalent) under ubuntu.

@iMurshaq: It is a laptop, but that's not the problem. In fact, for a small period, i use Win 7, Ubuntu 11.10 and Ubuntu 12.04, just to test it.

When log in under Win 7, the fan works pretty normal (sometimes really quiet, sometimes kinda fast, specially when playing games or using Illustrator, Flash, etc).

same thing in Ubuntu 11.10. A real quiet fan, until i start some heavy apps. 

So, i fell into the fact that something with Ubuntu 12.04 it's not working properly. Don't know if it's the CPU usage, the fan controller, or something else, but some OS behaviour is causing this issue

I appreciate your opinions, and i hope to solve it somehow

---

### Post by iMurshaq on 2012-05-09
Well you can always try my failsafe.
```
sudo apt-get update
```

---

### Post by javi_m on 2012-05-09
@iMurshaq: yeah, the whole system is up to date, it's always my first check.

I think (just saying), it could be something related with the fan controller. The cpu temp it's a little bit higher than ubuntu 11.10, but not THAT higher. So, i think the fan it's working at top speed, when it should be working a little bit slower.

---

### Post by javi_m on 2012-05-09
bump

---

### Post by tomtom12 on 2012-05-10
Same issue on my laptop Hp-DM4 - fan goes up and down a lot more than on my former install (10.10).  Nervous noise :(

---

### Post by TBABill on 2012-05-10
This is an oddball, but worth checking. Have you checked to see what CPUFREQ setting your machine is set to? You may have to install CPUFREQ-UTILS, but then you can ```
cpufreq-info
```Don't think you need sudo for that. If it says "performance" in the statement, then the CPU is held to max speed constantly. If it is set to "ondemand" then the machine increases CPU speed as necessary, but is about half speed under normal, non-strain conditions.

---

### Post by javi_m on 2012-05-10
Thanks @TBABill , I installed that package. All the CPU's says: The governor "ondemand" may decide which speed to use within this range.

So, i think it's set to "ondemand".

Thanks!

---

### Post by TBABill on 2012-05-10
Yes that sounds correct. Default is "ondemand" which scales the CPU as necessary. Was worth a shot to check, but must not be the issue. Do you have a proprietary driver for your video card available to install? They normally run cooler than the open source drivers.

---

### Post by javi_m on 2012-05-13
Sorry for the late replay

No, there aren't propietary drivers for my video card. i have the intel hd3000 integrated video card.

 Maybe it's just for a heavier video usage from the OS.

Thanks anyway. It's not so bad either (at least, i think so).

---

### Post by youngie on 2012-06-05
Same problem on a Dell desktop, CPU fan constantly going when not really doing anything. Doesn't happen in XP nor did it happen in 11.10 it's only since I upgraded to 12.04 so something in 12.04 is either using more CPU for no reason or the temps are being reported wrong. It happens just browsing files in Nautilus and when I open Firefox, then fan sounds about equivalent to medium to high CPU usage in XP. I'd say it sounds about the same as playing a 720p video.

---

### Post by daniaix on 2012-06-12
same problem here, on a Dell Vostro 3450, CPU i7-2640M @ 2,8 Ghz, 6Ghz Ram, Video card AMD Radeon HD 6630M and Mobile Intel HD Graphics.
I have also installed proprietary AMD drivers, but not any change. 
This is very annoying, since fans make a lot lot lot of noise. 
Hope someone can help us

---

### Post by hprem on 2012-06-13
I am also facing the same issue on Dell 3750. Any ideas how to stop the fan

---

### Post by velayo on 2012-06-16
Same problem on a HP G62 with amd cpu and gpu.  Minimal apps working and fan is on on high all the time.  I installed jupiter to control de cpu and even when I use the minimum settings I get the fan spinning like crazy.  

On 11.10 I could get almost 3 hours of battery usage with jupiter and powertop, on 12.04 it only lasts about an hour the most.  There is something eating up cpu cycles and constantly consuming power on 12.04.  I wiped ubuntu and installed deepin and still get the same issue.  

I can assure is not the laptop as I get almost no noise or fan activity on windoze 7.

---

### Post by Nico156 on 2012-07-04
same problem on my Dell xps15 L502

I installed psensor and temp of cpu1 and cpu2 are at 44° but the fan always run..

---

### Post by HolyMurderer on 2012-07-24
Same issue with a HP Probook 6460b, with Intel HD 3000 graphics. CPU temp is around 55-60º. I'm using Kubuntu 12.04.

The same laptop, which is a work laptop, also has dual boot with Windows 7, where fans work properly.

---

### Post by trulynon on 2012-07-26
Same issue here. HP Probook 4530s, i3, Intel graphics HD 3000. So far Jupiter is the best for me, however temps are still high. 

```
mariusz@mariusz-HP-ProBook-4530s:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +36.0°C  (crit = +128.0°C)
temp4:        +49.0°C  (crit = +128.0°C)
temp5:        +31.0°C  (crit = +128.0°C)
temp6:         +0.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +52.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +46.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +52.0°C  (high = +80.0°C, crit = +85.0°C)
```

---

### Post by ceciliasp on 2012-08-13
Same issue with my Lenovo G550....runnign Jupiter 0.1.4

---

### Post by joebuirski on 2012-10-16
I am having same problem with HP G62 with 12.04, Jupiter 0.1.7 etc
took it apart and cleaned tons of fluff out of the fan , still same problem (but surely better for the computer anyway), then saw this thread!

I've found that powering the laptop down, unplugging, removing the battery , then putting battery back in and restarting gives a few blissful minutes of silence from the fan... until sensors reads 50 degrees, the fan kicks in and then doesn't turn off, despite sensors reading 27-30 degrees.... bios settings are set to FAN ALWAYS ON <DISABLED>
irritating bug this

---

### Post by offgridguy on 2012-10-16
Interesting thread.

---

### Post by MrHotsauce on 2012-10-16
Iv'e had the same issue on my Toshiba l305 laptop, but I think I may know how to solve your issue. After boot on the login screen suspend you computer before logging in the power back on. That seems to solve my fan issues every time

---

### Post by universknight on 2012-10-30
same problem on my thinkpad x200s
```
universknight@laptop2:~$ cat /proc/acpi/ibm/fan 
status:        enabled
speed:        0
level:        2
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

speed shows 0
fan goes full speed no matter what level i set.
it will turn off when level set to 0
it can fix by restart, the speed will shows correctly but will goes full speed for a random time. and the speed will shows 0 again.

---

### Post by Farbklex on 2012-11-10
I have the same issue on a Dell Vostro 3350. I usually can't hear the fan when I use Windows 7 but with Ubuntu 12.04 it seems to be always running.
Cpufreq-info says that the CPU is ondemand so no problem there.

Looking for solutions.

---

### Post by jimmy7890 on 2012-11-19
HP ProBook 4520s, same problem.
Fan always on. Not on the highest speed, but it is definitely much quieter in Windows 8. Help?

---

### Post by jimmy7890 on 2012-11-19
I think installing laptop-mode-tools solve something, but i'm not sure that this is perfect. At least sometimes my fan stops for a while.

[http://samwel.tk/laptop_mode/](http://samwel.tk/laptop_mode/)

---

### Post by abdom on 2012-11-19
Same problem in my laptop Asus K50ij . Fan all the time runing and doing noise.

---

### Post by QuimNuss on 2012-12-23
Same problem here on an Ahtec computer.

Started happening on 10.04 one day.

---

### Post by amr.elhosiny on 2013-01-09
Here is what I have done,

I installed jupiter, set the CPU performance to "power save"
@ the login screen i select ubuntu 2D instead of ubuntu 3D
The CPU fan runs much lower than before. I do not feel any performance issues using the power save strategy. 
Before this, the fan was always on and very noisy and annoying even if just browsing the internet.But things are much better on Win7. My battery only lasts for 1:30 hours using ubuntu 12.04. While it lasts about 3:30 hours using Win7.

I'm having Dell Inspiron 5520.

---

### Post by aliaomt on 2013-01-24
I have the problem on 12.04 64 bit with asus eeepc 1215b
but it was ok on 12.04 32bit!

---

### Post by detroit/zero on 2013-01-29
Same here - cpu fan always running at or near top speed.

AT5IONT-I motherboard
Intel Atom D525 cpu
Nvidia Ion GPU

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +17.0Â°C  (crit = +100.0Â°C)
Core 1:       +18.0Â°C  (crit = +100.0Â°C)

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.12 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.35 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.09 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +11.90 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     5818 RPM  (min =  600 RPM)
CHASSIS FAN Speed:    0 RPM  (min =  600 RPM)
CPU Temperature:    +50.0Â°C  (high = +60.0Â°C, crit = +95.0Â°C)
GPU Temperature:    +40.0Â°C  (high = +60.0Â°C, crit = +95.0Â°C)
```

---

### Post by 73ckn797 on 2013-01-30
> **MrHotsauce said:**
> Iv'e had the same issue on my Toshiba l305 laptop, but I think I may know how to solve your issue. After boot on the login screen suspend you computer before logging in the power back on. That seems to solve my fan issues every time

Same computer. Fan runs all the time but system will shut off. It will nearly burn my leg around the fan area. Running in on demand mode with Gnome 3 (no effects). Unity has been completely removed.

---

