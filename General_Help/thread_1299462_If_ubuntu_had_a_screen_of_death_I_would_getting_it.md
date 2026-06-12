---
title: "If ubuntu had a screen of death I would getting it"
date: 2009-10-23
forum: General Help
---

### Post by Orfintain on 2009-10-23
So when I put any kind of strain on the system resources or sometimes for no-reason what-so-ever everything just shuts down on me ..

Maybe b/c I still have some Moblock stuff installed ? 

Maybe b/c of this 
[http://ubuntuforums.org/showthread.php?p=8155445#post8155445](http://ubuntuforums.org/showthread.php?p=8155445#post8155445)

Any suggestions?

---

### Post by elliotn on 2009-10-23
if d bsod was in ubuntu i would b getin it. my harddrive keep failing bt i keep connecting it without restart

---

### Post by tommcd on 2009-10-24
> **Orfintain said:**
> So when I put any kind of strain on the system resources or sometimes for no-reason what-so-ever everything just shuts down on me ..

I would first rule out a hardware problem here. How high is your CPU temp? Install **gkrellm** and **lm-sensors** and monitor your CPU temps under load.

---

### Post by Orfintain on 2009-10-24
Ok I installed the fancy system monitor, 

Dose it have a log file?

My CPU is usually maxed out when it crashes, from running multiple things at once but it's a fairly new machine and system monitor should be slowing down the task speed to match resources shouldn't it ?

---

### Post by phillw on 2009-10-24
> **Orfintain said:**
> Ok I installed the fancy system monitor, 

Dose it have a log file?

My CPU is usually maxed out when it crashes, from running multiple things at once but it's a fairly new machine and system monitor should be slowing down the task speed to match resources shouldn't it ?

There's a good resource for gk  here ...

[http://www.econowics.com/linux/241/how-to-install-gkrellm-on-ubuntu-linux/](http://www.econowics.com/linux/241/how-to-install-gkrellm-on-ubuntu-linux/)

And, it would appear that your system is not throttling back under load - gk should let you keep an eye on it. You may need to invest in a higher capacity cooler for your cpu. Are you over-clocking your cpu ?

Regards,

Phill.

---

### Post by Orfintain on 2009-10-24
Thanks for the replies

Do you know how to make it throttle back under load?

This is a personal machine.
I'm not over clocking it.
I'm not investing in higher capacity cooler.

My gnome panel crashes pretty often to which usually I can just restart it with the terminal ...

It's not just under high stress sometimes it's random with mild stress maybe from not rebooting in-awhile..?

sometimes it's just a few tabs in Firefox and open office. Virtual box is often problematic, but sometimes ripping one CD and re-encoding something unrelated will crash it,

---

### Post by tommcd on 2009-10-25
What is your CPU temp reported by gkrellm, or lm-sensors, or whatever you are using?
Any modern CPU and BIOS will shut the system down if it overheats to protect the CPU. Perhaps you could open up the case and clean out any dust with compressed air, especially the CPU cooler.
You can test if it is a overheating problem by opening the computer case and running the computer with an ordinary house fan blowing into the computer's innards, straight at the CPU. If the temps are lower and the system doesn't crash then it is a safe bet that overheating is the problem.
I recently lowered my CPU temps about 10 degrees at idle and ~15 degrees under load with an upgraded Cooler Master CPU cooler and Arctic Silver compared to the stock AMD cooler I was using.

---

### Post by Orfintain on 2009-10-25
It is around 15% and 54 deg C which seems kind-of hot for just running firefox and music .. maybe I do need to figure out how to get this laptop case open ..thanks

I have no idea what the temps where when it shuts down..

Does GKrellM have a log ?

---

### Post by Orfintain on 2009-10-25
Opening the case right... 

Well Now my wireless is broken because one of the those flat multi wire strip cords came unconnected (and no I didn't get to the intake for the cooling fan to clean it...)

I really should known better than to take apart a laptop 

expletive
expletive
expletive

At least I didn't break anything else

---

### Post by Orfintain on 2009-11-03
The update did not fix the problem 

often I will leave and come back to computer turned off that could only have crashed that wasn't doing any high-performance operations

---

### Post by ST3ALTHPSYCH0 on 2009-11-03
Dumb question. Is the fan even blowing air out of the case? You could be looking at a dead (or dying) CPU fan. Also, it's possible that the fan speed isn't being upped under load. I don't know what your BIOS might call it, but in AMD based systems there's a feature called "Cool and Quiet" that slows down the fan and underclocks the CPU when there's no load. If you have a similar option that throttles back fan speed, disable it. 
AT what RPM is your CPU fan spinning, anyway?

---

### Post by Orfintain on 2009-11-03
Yeah sometimes I can feel air coming out from fan when it's on.

As far as the actual speed I'm not sure how to figure that out ...I played with GKrelM some but I'm not seeing it.

---

### Post by tommcd on 2009-11-04
> **Orfintain said:**
> 
As far as the actual speed I'm not sure how to figure that out ...I played with GKrelM some but I'm not seeing it.
Did you also install **lm-sensors**?
After you install lm-sensors, run **sudo sensors-detect** and answer yes to all the questions it asks you. Then let it add the driver you need for the sensors to rc.modules.
Then when you restart gkrellm, right-click on it and choose "configuration". Under: builtins > sensors, it should (hopefully) give you the options to enable temps, fan speed, voltages, etc.
You can also run **sensors** from the terminal (after you run sensors-detect) to get the info on temps and stuff in the terminal.
The 54 degrees you mentioned does not seem to be too hot though. What model CPU is it?

Sorry you had problems disassembling your laptop. If you have problems getting it back together, this site may have info to help you:
[http://www.insidemylaptop.com/](http://www.insidemylaptop.com/)
They have tutorials on disassembling many models of laptops.
Other than heat and fan problems, I'm not sure what else could cause this.
Do you have other distros or Windows on the laptop? If so does it shut down under load on the other operating systems? This would help to rule out a software problem. If you don't, perhaps you could run a live CD for a while and see if it happens with a live CD.

---

### Post by Orfintain on 2009-11-04
2X  IntelCore2 Duo T5500 1.83Ghz

I don't think I have a fan speed sensor

I broke one of those multi pin connectors that goes to my indicator lights and wireless. I'm going to have to take it in I think maybe give it another shot possible just be a matter of reconnecting it, but I think I saw just the tape at the end with no connector 
The website doesn't quite have my model laptop

userh@jahbuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +51.0°C  (crit = +85.0°C)

---

### Post by Orfintain on 2009-11-07
I got a can of air spray and sprayed it out and that seems to have made all the difference in the world 

Thanks guys

(I also figured out how to re-attach the led indicator light and remember there is a manual one off switch for the Bluetooth/wireless on these laptops one of them got my wireless working again)

---

### Post by tommcd on 2009-11-08
Great news!
I'm glad you got your laptop back in fine working order.

---

### Post by Orfintain on 2009-11-08
> **tommcd said:**
> Great news!
I'm glad you got your laptop back in fine working order.

with this issue anyway

haha with linux there is always something to work on :(

[http://ubuntuforums.org/showthread.php?t=1162265](http://ubuntuforums.org/showthread.php?t=1162265)

---

