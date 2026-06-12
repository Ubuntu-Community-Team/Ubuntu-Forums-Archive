---
title: "xsensors / hdd temp display issue"
date: 2010-07-27
forum: General Help
---

### Post by jp351 on 2010-07-27
i am using the sensors applet for monitoring temperatures on my cpu, gpu, and the hdd... i love the applet btw...

i do seem to be having a small issue.........
after my computer is running for some time, the hdd temp displays 0 degrees
(i have it all set to display in celsius since i know in celsius the temp ranges and don't in fahrenheit)

..anyway, like i said, after some time the hdd temp displays 0 degrees... however, a simple restart will resolve this. i am using a desktop, so i'd hate to have to restart my system every 18 hours or whatever..

anyone have any ideas, suggestions, or quick fixes??

thanks! :)

---

### Post by P4man on 2010-07-27
open a terminal and run 

```
sudo hddtemp /dev/sda1
```

(replace 1 with whatever drive you want to monitor)

It should just report the temp. If it does; then its probably a bug in 
sensor applet. If it doesnt; first try waking up the drive:
```

sudo hddtemp -w /dev/sda1
```

Thats only for PATA drives and if you have just one drive; its not likely sleeping. So if that doesnt help; try killing the hddtemp deamon:
```

sudo killall hddtemp
```

then try again. If that makes it work, then its a bug in hddtemp. You may have to restart it in deamon mode for the sensors applet; not sure:
```

sudo hddtemp -d /dev/sda1
```

If that doesnt help; then it could be something with the bios or harddrive that just stops reporting.

---

### Post by jp351 on 2010-07-29
i only have the one hdd, it's a western digital caviar green; 500gb. it's practically brand new, 3 months or so old. it is a sata drive. like i said in the other post, it'll report the temp for a while, then it'll just quit. if i restart the system, it'll continue reporting as it's supposed to. 

if i right-click on the applet and go to properties, under sensors, there are 2 listed under the same hdd.. "/dev/sg0" and "/dev/sda" the sg0 is the one that quits reporting, but a few days ago, i've turned on the sda and it's still reporting, where the sg0 would have quit by now... anyone know if there's a difference between the two??

btw, if i click on help, it "quit's unexpectedly" and i'm given the option of reloading it or not. reloading it does not fix the issue.

---

### Post by dcstar on 2010-07-31
> **jp351 said:**
> 
.........
if i right-click on the applet and go to properties, under sensors, there are 2 listed under the same hdd.. "/dev/sg0" and "/dev/sda" the sg0 is the one that quits reporting, but a few days ago, i've turned on the sda and it's still reporting, where the sg0 would have quit by now... anyone know if there's a difference between the two??


The /dev/sgx are pseudo-SCSI designations for actual devices:

[http://manpages.ubuntu.com/manpages/hardy/man8/sg_map.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/sg_map.8.html)

Always better to use the actual physical device if you are having problems like that (although I don't know why your system changes, but those "Green" drives have aggressive power saving so that may be a factor).

---

### Post by jp351 on 2010-07-31
so, i should have xsensors report from "/dev/sda" not from "/sg0"?

like i said the other day, /sg0 is the one that quits reporting after a while and displays 0 degrees, whereas the /sda is still reporting, no problem..

---

