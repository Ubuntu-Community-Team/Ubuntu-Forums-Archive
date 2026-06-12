---
title: "Critical temperature reached (100 C), shutting down"
date: 2009-11-13
forum: General Help
---

### Post by bonnin on 2009-11-13
I have a T61p lenovo, when i work on my notebook all is well, when i step away for my desk for 20mins roughly i come back and my notebook is off. I do use a docking station this problem doesnt happen when im at home with no docking station. I can leave the notebook on all night and when i return its still on. I have searched through syslog and i do see the following i have a feeling pulseaudio is the culprit but why only on the dock.


Nov 13 12:45:01 fabian CRON[440]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Nov 13 12:47:55 fabian pulseaudio[2498]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov 13 12:47:55 fabian pulseaudio[2498]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 13 12:47:55 fabian pulseaudio[2498]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov 13 12:49:37 fabian ntpd[2392]: kernel time sync status change 6001
Nov 13 12:55:01 fabian CRON[8420]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Nov 13 12:58:09 fabian ntpd[2392]: kernel time sync status change 2001
Nov 13 13:05:01 fabian CRON[16088]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Nov 13 13:15:01 fabian CRON[23599]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Nov 13 13:17:01 fabian CRON[25124]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 13 13:19:00 fabian kernel: [14773.510780] **Critical temperature reached (100 C), shutting down.**

---

### Post by andrewc6l on 2009-11-13
My guess is that the CPU is running at a higher clock speed when it's plugged in (which it would be if docked), which means things get hotter. If that's the case, you'd see the same thing if it were just plugged in (but not docked).

That probably doesn't help solve your problem... maybe try throttling the CPU when plugged in? Not an ideal solution, but better than (literally) crashing and burning.

---

### Post by mattedm on 2009-11-15
Hi Andrew,

I have a X61 tablet with a docking station and am having the same problem:

thinkmatt kernel: [ 4066.118617] Critical temperature reached (128 C), shutting down.

I made a quick script to write the output of sensors program to a file every second and found this the next time the shutdown happened:

Sun Nov 15 16:34:47 MST 2009
acpitz-virtual-0
Adapter: Virtual device
temp1:       +74.0°C  (crit = +127.0°C)                  
temp2:       +74.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +75.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +75.0°C  (high = +100.0°C, crit = +100.0°C)  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       4234 RPM
temp1:       +74.0°C                                    
temp2:       +58.0°C                                    
temp3:       +58.0°C                                    
temp4:       +68.0°C                                    
temp5:       +32.0°C                                    
temp6:        +0.0°C                                    
temp7:       +41.0°C                                    
temp8:        +0.0°C                                    
temp9:       +59.0°C                                    
temp10:      +68.0°C                                    
temp11:       +0.0°C                                    
temp12:       +0.0°C                                    
temp13:       +0.0°C                                    
temp14:       +0.0°C                                    
temp15:       +0.0°C                                    
temp16:       +0.0°C                                    

Sun Nov 15 16:34:48 MST 2009
acpitz-virtual-0
Adapter: Virtual device
temp1:      +128.0°C  (crit = +127.0°C)                  
temp2:       +74.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +74.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +74.0°C  (high = +100.0°C, crit = +100.0°C)  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       4234 RPM
temp1:       +74.0°C                                    
temp2:       +58.0°C                                    
temp3:       +58.0°C                                    
temp4:       +68.0°C                                    
temp5:       +32.0°C                                    
temp6:        +0.0°C                                    
temp7:       +41.0°C                                    
temp8:        +0.0°C                                    
temp9:       +59.0°C                                    
temp10:      +68.0°C                                    
temp11:       +0.0°C                                    
temp12:       +0.0°C                                    
temp13:       +0.0°C                                    
temp14:       +0.0°C                                    
temp15:       +0.0°C                                    
temp16:       +0.0°C                                    

It seems that temp1 went from 74C to 128C in one second.  I find that hard to believe as I was working on my computer at the time of the shutdown and nothing really would warrant that.

I suppose it's possible that there is a hardware issue and the sensor maxes out for no reason, but given that this only started happening with the upgrade to 9.10, I think it is a software issue.

Can anyone help me diagnose or fix this issue?

---

### Post by cpcgm on 2010-11-30
Could any of you solve the problem? I've been having the same problems (X61s + UltraBay) for three days on a Arch Linux machine.

---

### Post by Ceretrea on 2011-06-26
I am getting this constantly when trying to to more then a few things at a time. I am currently trying to download WoW via Wine and the pc shuts down every 5 mins with this error. It shuts down immediately with this error should I attempt to run firefox at the same time.
If I am updating, and surfing at the same time I have also had this problem. 

My fan is working, the PC is well ventilated and I find it hard to believe the temperature is actually getting that hot. I am running 10.10, any thoughts?

To add to this, my BIOS thermal shut down is set at 80c and hasn't shut the system down once. How can the CPU be reaching 127c without tripping the Bios?

---

