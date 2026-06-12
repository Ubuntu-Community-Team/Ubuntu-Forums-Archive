---
title: "Fan doesn't come on after suspend in 10.04 Lynx"
date: 2011-03-27
forum: General Help
---

### Post by TheChumpion on 2011-03-27
This is my first post here, so I'm not really sure about what sort of responses I'll get. I'm actually sort of regretting the name I chose cause someone else uses it on another website and I can't seem to change it. But that isn't the real issue, so I'll get to the point.

I've had a problem with my Toshiba L355D running Karmic, and now Lynx, overheating for a while. It doesn't heat up as much as other peoples PC's that I've read about, where I've seen numbers like 100c, but it still is significant. When the computer comes out of suspend the fan setting is at its extreme lowest, and the computer, which has had it's bios updates and the kernel modules set to come on when it loads, don't seem to affect it.

The PC will continue to warm up until it reaches its emergency override when the fan comes on, about 80c, and then the temperature will drop, usually at a low of 50 to 60 if given space to cool and 62 to 72 if it sits on a bed. In windows it runs cool no matter what.

Now I love Linux so far since I converted a year ago, but I'm not happy about this. I can ignore other small things, cause Ubuntu hasn't failed me like how Vista did when it erased itself with disk cleanup or with updates causing it to be unable to start up. I can ignore the netflix problem, and WINE has made things easier in other ways, but this issue is the only one preventing my Ubuntu experience from being great. I've read about suspend bugs where Lynx doesn't suspend, but this isn't that, its that the fan controls don't work until the bios has to step in. I've tried to work with Toshiba Utils and still wasn't able to change it.

Is there a way to force the fan to come back on automatically after suspend? I don't mind it running loud if it protects the machine, I would prefer that it works at all.

---

### Post by Learning Linux 2011 on 2011-03-27
This is usually more of a BIOS issue.  

There should be settings in the BIOS to force fans to stay on all the time and/or set the temperature when they come on.

Have you actually ever gone into the BIOS by pressing a key when the computer first starts up?

---

### Post by TheChumpion on 2011-03-27
Already did. It didn't give me that option to control the fan, but I was able to change a setting so that the processor always runs at its minimum settings. That did make it cooler but it doesn't change the problem with the fan, which didn't ever have this problem with Windows.

The BIOS is completely updated too, and this problem is completely with Linux. I've put on the sensor app to tell me how hot everything is. This problem has been going on since the beginning of my Ubuntu use. I didn't have it with the other distro's I used.

I've been researching this for a while and unable to fix it completely. It was heating up faster before, but it still reaches unacceptable temperatures anyway. At one point it even got to 89 before the fan kicked in.

This particular problem is with the suspend somehow not causing certain kernel modules to come on after I return to desktop. I'm willing to bet that it's not the computer cause it didn't at all with Windows, as I can hear the fan sound come on as it starts up again. I'll go ahead and check the BIOS again anyway to see if there's something I missed.

---

### Post by Learning Linux 2011 on 2011-03-28
Yeah, sometimes those settings can be hidden pretty deep in the BIOS and/or have some weird thing you have to do to get to them.

Also, are you sure it isn't something new like the fan might be going bad? Perhaps alot of dust or just age?

I'm not an expert in Linux at the deeper kernel level.  Are the lights on your keyboard still on when you suspend? And/or does a fan stay on when you suspend?  Perhaps the computer isn't fully "suspending".  

Does it happen when you hibernate?  When you hibernate, it writes everything to the hard drive so you can literally unplug the machine and still save your settings.  Do you get a different result when you hibernate?  Try hibernating, then unplugging the computer, wait a few seconds, plug it back in, turn it on and see if that changes anything.

Also, does the computer have adequate air flow?  You mentioned something about a bed.  Those usually aren't good for laptops ;-)

---

### Post by Learning Linux 2011 on 2011-03-28
You could also try going into Ubuntu Software Center
and download a program called 'xsensors' to tell you more about your sensors.
I can't guarantee it will help, but it is worth a try.

---

### Post by TheChumpion on 2011-03-28
I tested the hibernate function and it worked perfectly, including the fan coming on as intended. In suspend the keyboard light for capslock turned off, confirming that it actually went to suspend.

the computer was cleaned internally 16 months ago, and maybe it needs to have that again, but I'm not certain I want to try that again since there was a new thermal paste job placed down. I could go ahead and try the vacuum trick to get whatever dustbunnies or gunk out, which I'll do before I rule out that this is a software thing, cause it was heating up just as much when it was cleaned.

At times, I set this thing on a laptop desk or just have it in my lap. I know it's not good to have it on a bed, but it wasn't an issue with Windows Vista. I've had it tilted with an object every time I use it with linux. It even runs finely if it is allowed to start up as usual, and the hibernation test showed me that it was not a complete problem with the hardware. I've done a test where I put it in the air with an external fan and this computer will still overheat anyway, reach 80 and the fan kicks in then.

The problem shows up with the computer fan specifically not running when the computer comes out of suspend, not anything else. I'm continuing to research ways to control the fan directly. What I need is to have a script run that forces the fan on when the computer comes immediately out of suspension. There are a set of toshiba utilities that exist but I've not been able to get an interface going, as they require a stronger understanding of the command line than I have right now. Still I'll continue on with this, since I was able to get it significantly cooler, it's just this one last glitch in the way. I'll say thank you for suggesting the xsensors, they're more responsive than the gnome sensors im using, though the gnome one is the only one actually registering the full temp of it.

---

### Post by Learning Linux 2011 on 2011-03-28
I found something else that could be helpful.

If you go to "System -> About Ubuntu" and type "fan" in the search box
it gives 2 results:

pwmconfig and a program called "fancontrol"

you might look into those too, they seem promising.  

pwmconfig gets your sensor information, and it looks like fancontrol might be pretty close to what you are looking for.

They are command line (Terminal) programs.  If it says you need to be 'root' to run them, type "sudo" before each command, which temporarily logs you in as root/administrator.  
As in: "sudo pwmconfig" without the quotes

---

### Post by TheChumpion on 2011-03-28
That looks like the best lead, thank you for finding it, everyone else was mentioning far more overwhelming measures like recompiling kernels and such.

---

### Post by hawthornso23 on 2011-03-28
It is an issue with many laptops. There are standards for how hardware is supposed to talk to the OS about things like temperature and power control. If people just followed the standards there would be no problem. But for some reason many laptops seem to have incomplete non-compliant and broken BIOSes and rely on specialised windows drivers  to do the job instead when windows is loaded. This is seriously annoying as without the cooperation of the hardware manufacturers it is hard to fix. It almost looks to me like the evil empire is paying OEMs to make their machines run badly on linux. These things do eventually get sorted, but if you have cutting edge hardware you might have to wait for a bit for a solution.

I have a similar issue with my Dell E6510 - although not as severe. The BIOS fan controller is far too slow to ramp the fan speed up in my opinion and tolerates much higher CPU temperatures than I would prefer.

---

