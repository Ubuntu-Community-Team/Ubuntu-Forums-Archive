---
title: "How well does Ubuntu handle multiple cores/threads (core i7)?"
date: 2012-03-29
forum: General Help
---

### Post by pcm2a on 2012-03-29
I am currently using a Samsung core i7 2630 laptop.  Windows 7 seems to do a <snip> poor job of managing my applications across my 4 cores/8 threads.  

My example is I am running a tomcat server in eclipse and doing development.  I also have a Windows 7 virtual machine running in VMWare.  On top of this I have various other things running, like any developer would.  With all of this going my system runs pretty slow.

I have an application to monitor my cores/threads.  At any given time one or two threads may be spiked and maybe 2% on a couple others.  This seems like poor management since I have so many apps running and my system is bogged down.

With Ubuntu is it possible to tell the system to use certain cores/threads when I start up a process?  For example I can really start hammering on this thing and not see my 3rd and 4th core being used.  So maybe I can tell VMware to always use core 4.  

If it's going to behave exactly like Win7 then there may not be a reason to try switching over to Ubuntu.

---

### Post by Mark Phelps on 2012-03-29
I have a multi-core processor, and while both Win7 and Ubuntu 11.10 work fine with it, they both work essentially the same.

Not only can you NOT specify which cores, you can't force an app to use more than one core.

So, if you're coming to Ubuntu because you want some fine-grained control that allows you to assign cores to apps, then you're in the wrong place.

---

### Post by dcstar on 2012-03-30
> **pcm2a said:**
> I am currently using a Samsung core i7 2630 laptop.  Windows 7 seems to do a <snip> poor job of managing my applications across my 4 cores/8 threads.  
........

[LIST=1]
[*]Laptops are not designed for intensive application uses, they are designed to be portable low-power use devices that ALWAYS perform with compromises to achieve those things.
[*]The Applications are the things that determine what CPU resources are used. The host OS is limited by what the original app writer has created.
[/LIST]

---

### Post by mcduck on 2012-03-30
> **dcstar said:**
> [LIST=1]
[*]Laptops are not designed for intensive application uses, they are designed to be portable low-power use devices that ALWAYS perform with compromises to achieve those things.
[*]The Applications are the things that determine what CPU resources are used. The host OS is limited by what the original app writer has created.
[/LIST]

process scheduling has _nothing_ to do with whether it's a laptop or desktop machine, and many laptops are designed for intensive use instead of portability anyway. :D

It's just a question of the applications themselves, a single-thread application can only ever run on a single core. And Ubuntu should do a decent job at distributing the applications between different cores whenever that's actually possible.

Also keep in mind that if an application isn't using full 100% of the core's CPU time, it might actually make sense to run another app on that core as well, and leave one core in sleep state. This allows reducing power usage and heat, and on new CPU's with turbo boost (or similar) capabilities, allows the active cores to run at higher speeds.

(and yes, you *can* manually tell a process to run on a specific core. Not that it would make any sense, though, the OS scheduler is sure going to do better job at this task than any human user would. If you feel otherwise, it's more likely because you aren't fully aware of how each of the processes is actually using CPU time)

---

### Post by pcm2a on 2012-03-31
> **Mark Phelps said:**
> I have a multi-core processor, and while both Win7 and Ubuntu 11.10 work fine with it, they both work essentially the same.

Not only can you NOT specify which cores, you can't force an app to use more than one core.

So, if you're coming to Ubuntu because you want some fine-grained control that allows you to assign cores to apps, then you're in the wrong place.
Thanks very much for the response.  That fine grained control is exactly what I was looking/hoping for.

---

### Post by 3Miro on 2012-03-31
Linux is the system of choice on servers and supercomputers, where high load has to be managed among not only cores, but clusters of machines. In my experience, Linux behaved much better under heavy load than any windows.

Having said that, pcm2a, you are not doing anything that requires huge load. Servers are low load, unless you are actually generating traffic. I am not sure about VM Ware's abilities to utilize multiple cores, but unless you are doing something intensive under the virtual machine, you should not see high load. Browsers and system processes are low load too. High load things are Games (Call of Duty, not Angry Birds), scientific software, compiling large projects etc. Writing code is not high load.

An application can be either single core or multi-core and most are single-core. If an app is single core, then it will use at most one core and that's that. If you have two single core apps that need a lot of resources, then they will use two cores and the rest of the cores will idle. Both Linux and Windows are smart enough to move system processes over to the idling cores so that the intensive apps can have each their core (for the most part). You do not manually manage that.

If you have a very intensive multi-core app, then it will launch a number of threads and the OS will distribute the threads among the available cores and again there is nothing for you to do. 

The number of cores utilized depends on the apps not OS, there is nothing for you to adjust manually.

---

### Post by dcstar on 2012-03-31
> **mcduck said:**
> process scheduling has _nothing_ to do with whether it's a laptop or desktop machine, and many laptops are designed for intensive use instead of portability anyway. :D
........

Laptop hardware is almost always compromised in so many areas that I can't begin to list them.

People seem to expect that laptops have the same "grunt" as other environments when they try to use them for intensive uses but the harsh reality is that they are designed for portability and virtually every other thing comes in behind that goal.

The only exceptions are the absolute top of the range laptops that are engineered for a level of performance that those willing to pay such prices require, not too many people are.

---

### Post by mcduck on 2012-04-01
> **dcstar said:**
> Laptop hardware is almost always compromised in so many areas that I can't begin to list them.

People seem to expect that laptops have the same "grunt" as other environments when they try to use them for intensive uses but the harsh reality is that they are designed for portability and virtually every other thing comes in behind that goal.

The only exceptions are the absolute top of the range laptops that are engineered for a level of performance that those willing to pay such prices require, not too many people are.
True, laptop CPUs are not as powerful as their desktop counterparts. But still, that has absolutely nothing to do with their ability to use multiple cores, or with process scheduling (which is what this thread is about).  Multithreading works *exactly* the same on a laptop CPU as on a desktop CPU, the only difference is that the individual cores don't have the same amount of computing power as the desktop CPU's cores would have.

(besides, there are loads of laptop models out there that are not designed for long battery life or small size/light weight, but more to serve as desktop replacements. Even mid-range ones. And of course a mid-range laptop can still have plenty more computing power than cheaper desktop system does, so making any generalisations simply based on desktop/laptop-axis doesn't make much sense even if we were talking about computing power instead of process scheduling and use of multiple cores... ;))

---

