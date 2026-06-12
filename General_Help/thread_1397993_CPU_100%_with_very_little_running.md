---
title: "CPU 100% with very little running"
date: 2010-02-03
forum: General Help
---

### Post by mansueti on 2010-02-03
I am running Ubuntu 9.10 on an old PC:  1900Mhz AMD K7 Athlon, RAM=512MB, Disk=65 GB available.  Ubuntu has this whole machine and there is very little installed on it except the vanilla 9.10 install.  I am a newbie when it comes to Linux and I am looking for assistance on a performance issue.  I am running Gnome.  I do not have any wireless stuff on this PC and no peripherals.
 

 The performance becomes very sluggish and it appears the CPU is being taxed quite a bit.  Memory utilization and swapping are very low.  When I first boot Ubuntu, CPU seem low.  The TOP command yields the following utilization:


<See attached Top1 image>

 

 If I then run the System Monitor, CPU utilization increases dramatically.  Xorg goes up to between 75% and 85%.  Memory utilization is only 37% and swapping is less then 1%.  See Below:


<See attached Top2 image>

                                  If I then run the System Monitor, CPU utilization increases dramatically.  Xorg goes up to between 75% and 85%.  Memory utilization is only 37% and swapping is less then 1%.  See Below:


<See attached Top3 image>

                                  If I then run Firefox without  System Monitor, performance is still very sluggish.  CPU usage is low if I am not using the Mouse. 


<See attached Top4 image>

                                  If I move the mouse over the Firefox window (note: just moving the mouse, no clicking of any links), CPU utilization increases dramatically.  This is with not Firefox activity since the page has already loaded.




                                  Seems crazy that moving the mouse would drive up so much CPU activity.
 

 If I then run Firefox AND System Monitor, CPU utilization goes almost to about 80%-85% (without any mouse movement):


<See attached Top5 image>

                                  If I start moving the mouse, CPU goes to 90% or so.  
 

 I am not using any fancy mouse or video drivers.
 

 Can anyone give me some direction to determine why so much CPU is being used.  Is the processor just too slow for Ubuntu?  Before I installed, I looked at the minimum specs and it appears I was well above that.  It appear System Monitor is a hog but why would Forefox with mouse activity use up so much CPU.
 

 Another problem I have is if I run Gnometris, it starts to launch but then it disappears from the bottom task bar (so I cannot play) but it is still a running process.  Not sure if this is related.  OpenOffice and other games seem to come up OK but the system is still slow.
 

 I look forward to any assistance anyone can provide.
 

 Thanks

---

