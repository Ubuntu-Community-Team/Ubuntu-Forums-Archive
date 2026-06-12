---
title: "False Warning: &quot;Battery Critically Low&quot; Help!"
date: 2012-01-08
forum: General Help
---

### Post by LanceRooke on 2012-01-08
How do I get rid of this false warning?  Every time I unplug my battery I get a pop-up warning that says the battery is critically low.... even when the battery is fully charged! I can not seem to find a solution to this.

---

### Post by JRV on 2012-01-08
What version are you using?
What hardware?
I had this problem a while back with 9.04 (Jaunty) and it went away when I upgraded.

If you provide the necessary information it will be easier for someone to help you.

---

### Post by LanceRooke on 2012-01-09
I'm using 11.10 on a Dell Inspiron 1501.

---

### Post by David D. on 2012-01-26
Any solution to this yet?

I am running 11.10 on an HP dv7 and have this problem.  If I unplug the laptop or there is a power fluctuation I get the battery critically low message and the laptop shuts down.  If I shut the laptop down or close the lid and let the laptop suspend before unplugging the power, then restart/open the lid I will get several hours on the battery.

---

### Post by Dngrsone on 2012-01-26
Try resetting the BIOS to factory condition.

---

### Post by xyzzyman on 2012-01-26
1501's came out in 2006. Are you sure the battery is still good? My 3 year old battery as you can see was rated for 71W's but now registers as 21.3W's but is more like 15-16W's by how long it lasts as it will run for so long and then drop to 0. 5-6 years on a battery for a notebook is a long time, especially if it's had alot of charge/discharge cycles.

---

### Post by jocefus on 2012-03-12
I have a brand new Alienware m14x running 11.10. As soon as you unplug ac power, it says the battery is critically low and will suspend or shutdown. However if you boot the machine on battery, everything runs fine.

---

### Post by chanxebyshev on 2012-05-09
I am also having this problem on a new computer,
Toshiba satellite P755.

I had the problem with 11.10 and it still exists in 12.04

The computer is fully charged

I unplug it and I get the message in picture and the battery time remaining reads 4 mins.
 

Within 30 seconds the battery figures out that it is full and says I have 4 hours of battery time left.

---

### Post by chanxebyshev on 2012-05-30
This trick worked for me in 12.04 and originally intended for 11.10, thanks to adonis
[http://askubuntu.com/questions/83207/regardless-of-battery-charge-when-unplugged-ubuntu-displays-critical-battery-me](http://askubuntu.com/questions/83207/regardless-of-battery-charge-when-unplugged-ubuntu-displays-critical-battery-me)

"open dconf-editor: org > gnome > settings-daemon > plugins > power and just uncheck: use-time-for-policy"

---

