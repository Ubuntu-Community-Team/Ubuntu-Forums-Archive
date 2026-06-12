---
title: "Ubuntu 10.04 (lucid) - Fan control"
date: 2010-09-30
forum: General Help
---

### Post by Gordonisnz on 2010-09-30
Hi.

Is there a graphical interface for a Fan control ?

IE, So I can easily see in 1 place, what is going on.


My fan is running 100% - & my Core Temp is going up  - If its too high, my monitor/PC turns off :(


I found this :-

[http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/)

(This thing asks lots of YES/NO questions & produces lots of text output in a terminal screen.... (very cumbersome to use / read the details of any results...)

My fan went low - & my temp went low   

but now its running 100% now & my temperature is going up again.. 


I'm NOT doing any hard-fast mathematical calculations or web searching etc - I only have a few screens open & theyre just sitting there - Not doing anything 

System tools show i'm not running 100% CPU on anything...

---

### Post by Gordonisnz on 2010-09-30
During my travels on the net, I found EEE

- However theres a problem, & I can't un-install it (via synaptic)

---------------------------------
E: eee-control: subprocess installed post-installation script returned error exit status 1
---------------------------------


is EEE important ?

How can I (un/re) install ?

---

### Post by no2498 on 2010-09-30
install htop
open a terminal type htop click enter it tells you how to install it
now just type htop click enter
see what is running to make the computer run hot


as far as the ee program  you may turn it off in the startup menu 

never slow a fan yourself find out why its running and fix it
let the system do its job

hope this helps

---

### Post by kDDs on 2010-09-30
eee-control is a specialist program designed for eee pcs (asus netbooks) it's very unlikely it will work with other systems, and could cause damage.

---

### Post by TBABill on 2010-09-30
If you are using an open source video driver it is likely your GPU is running at max (100%) constantly, regardless of what you are doing. Your system may be set to "performance" for CPU frequency scaling, which keeps your CPU cycling at max frequency as well. Those two items will bring up your heat levels regardless of what you are doing.
 
If you have an available proprietary video driver you could try enabling it. you can also go to the top panel, click "add to panel" and select CPU Frequency Scaling applet. Then when it's on the panel just left click it, select ondemand (or powersave, but I use ondemand) and see if that helps any. It won't tell you anything about your fan performance, but it may help reduce the heat levels some. if your machine is cutting off you are hitting critical temp limits, probably along the 90-110 degrees C level...dangerously high for your hardware.

---

### Post by tech7 on 2010-09-30
hey, what's your make/model??

check this out for now..
[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

---

### Post by Gordonisnz on 2010-09-30
> **kDDs said:**
> eee-control is a specialist program designed for eee pcs (asus netbooks) it's very unlikely it will work with other systems, and could cause damage.

Ok, 

How do I remove/ eliminate eee ??
I've tried  Synaptic  & I always get an error code (1) if I emove it

> 
 E: eee-control: subprocess installed pre-removal script returned error exit status 1





I installed htop - I'm running 1% CPU, & my temp goinng up..


NVIDIA X SERVER SETTINGS >> GPU 0 (GeForce 9800 GT)
>> THERMAL SETTINGS 

Fan speed 100%,   Core temp 91c (Going up...)


Whastever NVIDIA is - its getting hot...


I thought Linux was supposed to be problem-free

---

### Post by kDDs on 2010-10-01
No OS is "problem free", especially not linux.

Try downloading an older .deb package from here:

[http://greg.geekmind.org/eee-control/deb/](http://greg.geekmind.org/eee-control/deb/)

Install it, and then attempt to uninstall it.

"NVIDIA" is the manufacturer of your graphics card. There's a chance the program isn't reporting correctly. You'd know if a 9800GT was running it's fan at 100%, it will be VERY loud.

Do you have the Nvidia proprietary driver installed? The program "nvidia-settings" can detect the temperature of the graphics card.

---

