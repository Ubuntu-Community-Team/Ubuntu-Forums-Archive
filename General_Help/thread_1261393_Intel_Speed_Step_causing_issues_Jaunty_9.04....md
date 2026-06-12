---
title: "Intel Speed Step causing issues? Jaunty 9.04..."
date: 2009-09-08
forum: General Help
---

### Post by dtrot55 on 2009-09-08
I am currently running the computer in my signature and from the very beginning when I installed 9.04 I noticed that when I did stuff that would require a little more processing power that my cpu fan would go nutz and I would notice the computer stuttering or laggin when processing certain things..like web sites and moving windows...so i disabled compiz and i disabled speed step...

well come to find out disabling speed step sets your processor at the lowest possible setting...so under this setting things would run slow..sites would load and scroll slow...so i reenabled speed step after adding another gig of ram to my laptop and giving me a 4 gig swap and still getting this same issue....though if i disable it, it all goes away but then i get poor performance....any ideas anyone???

---

### Post by Whiffle on 2009-09-08
If you add the little applet to the taskbar that monitors your cpu frequency, what does it do when you give it work to do? 

Also, could you post the output of "lsmod"?

EDIT: 
an easy way to make "work" for the processor is to do "yes > /dev/null" in the terminal.  Ctrl+C stops it.

---

### Post by P4man on 2009-09-08
Might be worth trying to clean the fan(ducts). I figure the slowdown with speedstep enabled on cpu heavy tasks is the processor throttling to prevent a meltdown. I think (but not sure) this should show up in your logs though, have a look at them in system > adminstration > log file viewer.

---

### Post by dtrot55 on 2009-09-08
> **Whiffle said:**
> If you add the little applet to the taskbar that monitors your cpu frequency, what does it do when you give it work to do? 

Also, could you post the output of "lsmod"?

EDIT: 
an easy way to make "work" for the processor is to do "yes > /dev/null" in the terminal.  Ctrl+C stops it.

can you fill me in on the applet for the taskbar...like how to get it there?

also can i get the line of code to run lsmod or do i just type in lsmod?

---

### Post by dtrot55 on 2009-09-08
> **P4man said:**
> Might be worth trying to clean the fan(ducts). I figure the slowdown with speedstep enabled on cpu heavy tasks is the processor throttling to prevent a meltdown. I think (but not sure) this should show up in your logs though, have a look at them in system > adminstration > log file viewer.

What would i be looking for in the log viewer?

---

### Post by P4man on 2009-09-08
> **dtrot55 said:**
> What would i be looking for in the log viewer?

not sure.. try triggering the problem by running some cpu intensive stuff, when it starts slowing down/acting up then look at the corresponding times in the logfiles. Id guess it has "thermal" or "critical", "temperature" or something in it? But any other error you see might be relevant or interesting too.

---

### Post by dtrot55 on 2009-09-08
well i added the cpu freq monitor and it said i was running at 600mhz....its a 1.8ghz processor!!! this processor does support scaling so whats up?

---

### Post by P4man on 2009-09-08
> **dtrot55 said:**
> well i added the cpu freq monitor and it said i was running at 600mhz....its a 1.8ghz processor!!! this processor does support scaling so whats up?

It should be working at 600 Mhz when you're not making it work hard. it saves battery (and heat) :)  To enable scaling, Speedstep must be enabled in the bios, and then it will speed up to 1.8 GHz when it needs to.

---

### Post by dtrot55 on 2009-09-08
> **P4man said:**
> It should be working at 600 Mhz when you're not making it work hard. it saves battery (and heat) :)  To enable scaling, Speedstep must be enabled in the bios, and then it will speed up to 1.8 GHz when it needs to.

This computer has no battery as the battery does not hold a charge anymore..i have pulled it out of the system...so  i only run it when plugged into the wall

---

### Post by XCan on 2009-09-08
Put some load on it and see if it scales itself up to 1.8 GHz, it better do it.

---

### Post by Whiffle on 2009-09-08
Try doing:

sudo apt-get install cpufrequtils

I just noticed that they weren't installed by default on my laptop...I installed them and now its working correctly.

---

### Post by dtrot55 on 2009-09-08
> **Whiffle said:**
> Try doing:

sudo apt-get install cpufrequtils

I just noticed that they weren't installed by default on my laptop...I installed them and now its working correctly.

I did install that a little before your post...does it do stuff on its own or are there some settings i have to play with..because i really dont  see where it is located to play with???

---

### Post by dtrot55 on 2009-09-08
> **Whiffle said:**
> If you add the little applet to the taskbar that monitors your cpu frequency, what does it do when you give it work to do? 

Also, could you post the output of "lsmod"?

EDIT: 
an easy way to make "work" for the processor is to do "yes > /dev/null" in the terminal.  Ctrl+C stops it.

here it is...don't really know what this does but hopefully it can help you help me :)

[IMG]http://i103.photobucket.com/albums/m142/dtrot55/lsmod.png[/IMG]

---

### Post by dtrot55 on 2009-09-08
although I am wondering......I just downloaded and burned the Dell Ubuntu cd and when the cd was loading the CPU fan started going nutz..so wondering...this a mobo thing or a ubuntu thing...and i really really dont want to leave ubuntu due to this..any ideas?

---

### Post by Whiffle on 2009-09-08
Hmph.  They must have changed how frequency scaling works...because there used to be a module for it and now I don't see it.  Figures...I'll post back if I  come up with anything.

---

### Post by dtrot55 on 2009-09-09
I took apart the laptop and pulled the mobo battery...also checked my fans and heatsinks..put it back together...did a fresh reformat of Ubuntu 9.04 and stressed the system...It did kick in the fan but not nearly as loud and over time when it wasn't being stressed the fan calmed back down...So I think this may have fixed the issue I was having...but not for sure totally...still testing...but thanks to everyone for their help...I will continue this thread for others in case they have the same issue.

Things that have kicked the fan into high gear:

Firefox with live flash stream left on for awhile
Gimp editing

---

### Post by orange_roughy on 2009-09-22
I've had numerous problems with speed step / cpu frequency scaling in Ubuntu Jaunty (9.04). My dual-cores are 2.4 GHz but Ubuntu insists on keeping them at 800 MHz each. The CPU Frequency Scaling App doesn't respond to requests to increase the speed. The system is on AC all the time. I only use it for web browsing so load is minimal. I just want to disable the *!#^$%@& thing but cannot for the life of me figure out how.

Why did I a buy a 2.4 GHz dual-core machine? I should have spent 1/4 the money on an ancient 800 MHz PC.

---

### Post by XCan on 2009-09-22
Although this is not a fix for the Ubuntu's frequency scaling thingy, have you tried disable speedstep from BIOS?

---

### Post by orange_roughy on 2009-09-22
> **XCan said:**
> Although this is not a fix for the Ubuntu's frequency scaling thingy, have you tried disable speedstep from BIOS?

Thanks for the reply. As is mentioned either in this thread or some of the others concerning speedstepping / frequency scaling, disabling speedstepping in the BIOS fixes the CPU cores at their loweset possible CPU frequency (in my case, 800 MHz). I've confirmed this.

Thanks

---

### Post by XCan on 2009-09-22
Ah, sorry old thread, I must've read it before and forgot while I used the "go to first unread thingie button".

---

### Post by orange_roughy on 2009-09-22
> **XCan said:**
> Ah, sorry old thread, I must've read it before and forgot while I used the "go to first unread thingie button".

I was wrong. It's not mentioned in this thread. But it's mentioned in other threads on the topic in these forums, and I've confirmed it myself: disabling in the BIOS forcing the CPU cores to their lowest frequency.

---

### Post by gidyeo on 2009-09-29
To disable "ondemand" cpu governor see the following thread:

[http://ubuntuforums.org/showpost.php?p=7394265&postcount=7](http://ubuntuforums.org/showpost.php?p=7394265&postcount=7)

Then reboot the system.

To toggle "ondemand" cpu governor:
[http://brainwreckedtech.wordpress.com/2009/05/29/ubuntu-9-04-bug-ondemand-doesnt-scale-cpu-speed/](http://brainwreckedtech.wordpress.com/2009/05/29/ubuntu-9-04-bug-ondemand-doesnt-scale-cpu-speed/)

:)

---

### Post by orange_roughy on 2009-10-03
> **gidyeo said:**
> To disable "ondemand" cpu governor see the following thread:

[http://ubuntuforums.org/showpost.php?p=7394265&postcount=7](http://ubuntuforums.org/showpost.php?p=7394265&postcount=7)

Then reboot the system.

To toggle "ondemand" cpu governor:
[http://brainwreckedtech.wordpress.com/2009/05/29/ubuntu-9-04-bug-ondemand-doesnt-scale-cpu-speed/](http://brainwreckedtech.wordpress.com/2009/05/29/ubuntu-9-04-bug-ondemand-doesnt-scale-cpu-speed/)

:)

Was that supposed to help? It didn't :)

Ubuntu simply doesn't detect properly when my AC power is attached vs. battery. Maybe it's a problem with my hardware, I don't know, but I want to keep the CPUs pinned to their maximums all the time because of this. Any ideas?

---

### Post by dtrot55 on 2010-03-25
Just re-installed Ubuntu 9.10 on my laptop and the issue has returned...after anything like browing for awhile in Firefox or even ubuntu updates...my processor fan kicks in like its life depended on it and it is LOUD!!!  Disabling Intel Speed step only makes my laptop run like a computer made in 1990.  It's been awhile since I first posted this..so was hoping someone might have a new fresh idea.

Thanks!

---

### Post by dtrot55 on 2010-06-26
Just to update this thread...

I took the laptop pretty much all apart..took off all fans and cleaned them...also removed the thick layers of dust on the heat sink of the processor.  

So far after running what usually kicks this issue I was having in, I have yet to have a LOUD fan.  I don't know if that really fixed it...I had installed cpufreqd before I shut down to take the laptop apart.  So I think I can say this has been solved on my end.

---

