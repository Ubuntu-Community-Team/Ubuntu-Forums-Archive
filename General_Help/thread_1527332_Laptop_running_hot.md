---
title: "Laptop running hot"
date: 2010-07-09
forum: General Help
---

### Post by JugglinPhil on 2010-07-09
My Laptop, a not too old Compaq, is acting strangely, in the sense that it is running hot really quickly. As soon as it is going for a while, it is getting pretty loud and you can barely touch the keyboard, don't think that it is any good for the machine.
Now the thing is it does not do that when running Windows, so I assume Lucid is sort of killing it. 
May it be too much stuff running in the background or not enough space on the drives?
Would be great to have some opinions on this issue.

---

### Post by TBABill on 2010-07-09
I have several laptops with different distros running on them. They all run hot until you make some configuration changes, but they're easy. You need to enable CPU scaling if your machine/processor are capable of doing so. Install CPUFREQ from Synaptic and in a terminal configure it to "ondemand" instead of "performance". Performance leaves it operating at max frequency on the CPU...unnecessary unless the system needs it, which is what "ondemand" takes care of. It idles at lowest speed unless the system demands more processing power, then it scales as necessary. This reduces CPU heat.
 
More importantly is to install the proprietary driver for your video card. People will claim you need to clean fans, remove debris from ducts, etc. That's not going to help if your machine is running cool under windows. If it was any OS and it ran hot, then you would have a hardware issue. You obviously do not. Install the proprietary driver for your card and you should immediately begin to cool back down. The open source drivers suck for laptops because they cannot scale your GPU and they run at max constantly. 
 
Lastly, make sure you are running Sun Java, not the open Java. It does make a difference for heat, but I did not realize it at first. This last step helped me get my machine down in the 40s and 50s Celcius. Only under heavy Adobe Flash applications (bubblebreaker.net) do I get hot, sometimes up into the high 60s or low 70s (or when I finally can't stand the heat anymore). I keep my fans unobstructed and the ducts clear, but flash just causes heat.
 
Hopefully some or all of those can help you. Once you install CPUFREQ, just type cpufreq-set --help and it will tell you how to set it for your desired setting. Most likely you just need to type > cpufreq-set --governor ondemand. Once you do that just close the terminal and enjoy. To see what you are running at, install an applet or widget that monitors temps. Or type "sensors" in a terminal and it will report your temps. Note: you do need to sudo in order to execute the change...must be root.

---

### Post by cloyd on 2010-07-09
If the above doesn't work, look at this:
[http://ubuntuforums.org/showthread.php?t=1518658](http://ubuntuforums.org/showthread.php?t=1518658)
All of this may not concern you, but the the part on the 2.6.34 kernel cooled my machine down considerably.  Don't know that acerhdf will help you any. Wonder if it is for specific hardware? (I don't know.)  It allowed me to set my fans to come on earlier.

However, I think I'd like TBABill's suggestion if I could use it, but I can't. My machine doesn't support CPU scaling, and I've found nothing that will let me underclock it.

---

### Post by JugglinPhil on 2010-07-12
Alright I installed it and ran the command, but I am not sure if it did anything. I think it is running slightly cooler, but that might as well be my imagination..
Also, how do I change my java version? Remove and reinstall through Synaptic?

---

### Post by dragos240 on 2010-07-12
> **JugglinPhil said:**
> Alright I installed it and ran the command, but I am not sure if it did anything. I think it is running slightly cooler, but that might as well be my imagination..
Also, how do I change my java version? Remove and reinstall through Synaptic?

No need to reinstall. Do upgrade instead!

sudo apt-get update
sudo apt-get upgrade sun-java6-jre

---

