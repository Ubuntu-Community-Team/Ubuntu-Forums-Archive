---
title: "Ubuntu vs Windows 7, Laptop Fan Heat"
date: 2010-10-18
forum: General Help
---

### Post by syga on 2010-10-18
I have windows 7 and ubuntu 10.10 dual boot on my laptop. Did a fan test to see which one runs cooler. Both were run on base installations, idling with just the desktops showing. Ubuntu was set to powersave.

Ubuntu: fan turns on every 6.5 to 7.5 minutes.

Windows: fan turns on every 17 minutes.

I'd rather support Ubuntu, but if it runs hotter, fan turns on more frequent which in turn will decrease battery life, then I have to use Windows :(

---

### Post by matsuzine on 2010-10-18
To know for sure, you almost need to install temperature monitoring software in both os to check.  However, I read that win 7 had seen some significant work optimizing this area, so it may actually be doing a better job with power saving.

---

### Post by Mark Phelps on 2010-10-18
Are you monitoring CPU temps?  

I suspect that the CPU MAY be running hotter in 10.10, which would account for the fan coming on more frequently.  But if that is true, it will also shorten the life of your CPU if it overheats as a result.

In MS Windows, I've used SpeedFan to monitor fan speeds and chip temps.

In Ubuntu, you need to install lm-sensors, then open a terminal and run "sudo sensors-detect" and reply "y" to all the questions, reboot, and once up again, open a terminal and run "sensors".  You should then see a long list of temps.

I would keep an eye on the temps in Win7 as compared to Ubuntu.  I'd be more concerned about Ubuntu running hotter than with the fan running more often.

---

### Post by TBABill on 2010-10-18
I think you'll find Ubuntu does in fact run hotter on most any machine. It is not normally a large difference, but flash apps do tend to eat a lot of CPU, for example, because flash does not yet support hardware acceleration. That makes your CPU do most of the work, which creates unnecessary heat and power consumption compared to Windows.
 
There are steps you can take to lower heat, which is what you need to do so your fans do not run so much. Fans respond to sensors, which respond to heat. The heat is the problem, not the fan. If the fan is working properly it will run anytime it is triggered, which is probably more often than in Windows, especially during internet usage with flash and java enabled sites.
 
I always make sure to install the proprietary video driver for my machine, switch to adobe flash (not Gnash), install sun java and make sure my cpu frequency scaling is set to ondemand. That's on every distro install. I believe the kernel is set now to default to ondemand, or at least it is that way in Ubuntu, so that helps. There is an applet you can add to the panel to watch your CPU frequency change as necessary.

---

### Post by Quackers on 2010-10-18
Which fan is turning on? CPU or GPU? It may be a graphics thing.

---

### Post by a-user on 2010-10-18
what gpu do you have installed?
are you using the open source drivers or proprietary ones?
do you use compiz (glx accelerated desktop effects)?

there are several tweaks you can achieve lower cpu usage i many situations. some of them may also lower gpu usage / heat.

i was very impressed what difference it made putting the following options in the device section of my xorg.conf using nvidia proprietary driver:
Option "UseEvents" "True"
Option"BackingStore" "True"
Option "DamageEvents" "True"

especiialy the frist two significantly reduced my cpu load. but it is known that in older version of xorrg/compiz and drivers it cuold lead to problems under special situations. it is to expect that this has been fixed. but it is worth to note.

---

### Post by theozzlives on 2010-10-18
I don't know, deciding battery life over security, stableness, and reliability to be the factor in what OS you use. If my OS has those features and I use a little more battery, so what! I'd rather have that than Trogens, Viruses, and other Malware.

---

### Post by TBABill on 2010-10-18
+1. Great perspective on that comment theozzlives. I would take the frustration of plugging in more often any day over threats to Windows.

---

### Post by Quackers on 2010-10-18
Me too, definitely :-)  Actually I am doing, as I don't run power saving measures when on battery.

---

### Post by nhianho on 2010-10-18
I've noticed that ubuntu runs hotter than win 7 as well. At idle, my laptop runs at 39 deg Celsius with win 7 but at 45 with ubuntu 10.10. I think it's the reason why ubuntu consumes more battery than win 7.

---

### Post by colin.p on 2010-10-18
and just to confuse the issue even more, I have 7 and 10.04 on a Dell 1545. Using Firefox in 7, my temps run around 55-70 and the fan will come on at 65 or so and run until down to 45 or so and keep cycling when the temps start climbing. 10.04, on the other hand runs around 45-50 and the fan rarely comes on. Occasionally, the temp will go up, usually if I am copying large files, as an example, and the fan kicks on.
When I got this laptop in May, the temps were slightly higher in Ubuntu, but a couple of kernel updates ago and now Ubuntu actually runs cooler.
Now this laptop is a low end model with Intel cpu and graphics, no gaming machine.

---

### Post by syga on 2010-10-19
Update:

I read through the replies and did some more googling on this subject. 

1: I had installed the cpu frequency applet and set it to powersave. But a few minutes later, it would reset itself to ondemand. Can't find any information why its doing this

2: Installed rovclock to underclock my ati graphics card.

3: Installed the 64 bit edition of ubuntu 10.10, before I had the 32 bit edition installed. I have the AMD Athlon chip. I was reading that the 32 bit edition kernel runs at 1000 hz and the 64 bit and server editions run at 100 hz. 

4: If I keep resetting my cpu to powersave, underclock my graphics card and installing the 64 bit version of Ubuntu made a minor improvement.

5: Installed Laptop Mode Tools. Did some configuring with it. Now my cpu frequency stays on powersave. Now my laptop fan cycled after 17 minutes of idle time (originally it was 6.5 to 7.5 minutes). Windows 7 cycled after 15 minutes. 

Installing Laptop Mode Tools and configuring it made a huge improvement :)
The hot running laptop is now FIXED!!!
Windows 7 is now GONE!!!

---

### Post by Quackers on 2010-10-19
Lovely :-)

---

### Post by TBABill on 2010-10-19
Outstanding news! Now others can search and possibly benefit from the steps you took as well. :)

---

### Post by nhianho on 2010-10-19
@syga: thanks for your informations but I have a question for you ( or anybody who can answer). I'm just a newbie to ubuntu.

I recently installed laptop mode tools via synaptic package manager but I really dont know how to run it. I've been searching it in the menu but couldn't find anything.

Any help will be truly appreciated.

---

### Post by ivarn on 2010-10-19
> **a-user said:**
> i was very impressed what difference it made putting the following options in the device section of my xorg.conf using nvidia proprietary driver:
Option "UseEvents" "True"
Option"BackingStore" "True"
Option "DamageEvents" "True"

If I add these lines to my xorg.conf file, under what section do I put them?
InputDevice, Monitor, Screen or Device?

---

