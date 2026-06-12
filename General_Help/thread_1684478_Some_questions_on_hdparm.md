---
title: "Some questions on hdparm"
date: 2011-02-09
forum: General Help
---

### Post by bryanchicken on 2011-02-09
First off, sorry if this is in the wrong forum. I had a choice between this and 'hardware & laptops'.

I'm by no means a linux expert, but i'm not a complete noob either.

I'm having a tough time getting my drives to spin down on my xbmc installation (on top of ubuntu minimal 10.04).
I had this working previously on debian where things were done a bit different (/etc/init.d/hdparm and /etc/hdparm.conf were all that was needed).

On ubuntu i modified my /etc/hdparm.conf to add 'spinddown=120' like i did in debian, but the disks didn't spin down. Nothing was accessing them as i could run hdparm -Y /dev/sdX and they would stay in standby.
I also tried the 'apm=120' setting.

Then i noticed that there is no init.d script any more, so i'm guessing my settings aren't being applied at startup.
So, i did some reading and found that in ubuntu hdparm now uses udev. However there is nothing in /etc/udev/rules.d relating to hdparm.

To add to my confusion there is also a file in /etc/apm/events.d that seems to set hdparm values. I added some echoes to a file into this and its seemingly never called though.

What is the correct way to get hdparm working?

Currently i've added a couple of 'hdparm -S120 /dev/sdX' lines to my rc.local and also created a script in /etc/pm/sleep.d to set on resume from sleep.



One other small question. I keep seeing the -B option with regards to spinning down disks. I can't seem to find what exactly that means other than 'Set Advanced Power Management feature, if the drive supports it' which means little to me.
Also, what do that values of 1-255 represent for that setting?


Sorry for the long essay, i've spent ages trying to work all this out :confused:

Thanks

---

### Post by Cyber1000 on 2011-02-09
Hello!
I too have my problems with hdparm, but perhaps I can give a little bit input.
 
I would try to set the params directly with hdparm, if I'm correct they will be lost on reboot, no fiddling with the configfiles or even rc.local before you know what you do and if it even works like this.
 
if you want to find something out in linux like the -B parameter you should look at the manpage ("man hdparm"), it will show the following: "Query/set Advanced Power Management feature, if the drive support ...". In short every newer harddisk has some power saving capabilities. 1-127 will allow power management to spin down, 128-254 will only save power. 1 will give you low I/O on disk, but good powersaving, 254 will give you nearly no powersaving, but high I/O throughput. 255 will disable this feature. hdparm -B 255 /dev/sdx (hdparm -B /dev/sdx will give you the current value)
 
Instead of spinddown=120 you could try "hdparm -S 120 /dev/sdx" on your commandline, it will do the same, until you reboot. If this works (your disk should spin down after 10 minutes) you may enter it in one of the configfiles. I think /etc/hdparm.conf should be fine then, in /etc/apm/events.d/ you can put a script, that will be called, if an event will be triggered. But as said before that I would use the commandline thing to test.
 
To spin down your harddrive immediately (to test if the spin down itself works as aspected) try "hdparm -y /dev/sdx" (Warning use only the lower y, not the Upper case Y if you are not sure). If that works, but "hdparm -S 120 /dev/sdx" doesn't then something accesses your disk and therefore it can't spin down.
 
**So and thats the point where your question stopps (for now :-) ) and my question starts:**
"hdparm -y /dev/sdx" works, but 
"hdparm -S 120 /dev/sdx" doesn't. In iotop I can't see anything helpful...
My drive has lvm, one mount of this lvm, and some bind mounts from there. Should I unmount all and deactive lvm? I'm not accessing the drive and I don't know any program which could ... (It's not my system drive!). How may I find out what blocks my spin down?

---

### Post by Cyber1000 on 2011-02-20
No answer? Neither of threadstarter nor someone else?
Have you solved your (and my) problem?

---

