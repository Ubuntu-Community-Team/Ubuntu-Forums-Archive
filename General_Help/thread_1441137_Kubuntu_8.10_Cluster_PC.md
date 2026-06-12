---
title: "Kubuntu 8.10 Cluster PC"
date: 2010-03-28
forum: General Help
---

### Post by ShadeS_07 on 2010-03-28
Hi, I want to know if it's possible for me to make a cluster computer with my Kubuntu 8.10 Linux distro...

Basically, I want to upgrade my computer by combining 2 or more computers to have myself a more powerful computer. If it's possible to do such, please tell me how... in details/step-by-step if you don't mind, but any useful help would of course be highly appreciated... ^^

So, let me put here the details of what I have right now.

Well, actually this is my first time doing such, which means I haven't done something like this before. I'm in a learning stage right now so I'd like to start from only 2 computers, then I'd expand my nodes into a greater number when I get into the point where I totally know what to do... In the meantime, 2 nodes for a cluster. -_+

I have 2 PC's... One is my computer and the other one is my dad's computer... My PC has a 2.80 GHz Intel Pentium 4 processor with a 1 GB DDR1 SDRAM and my dad's PC has a similar processor to the one I have and a 512 GB SDR SDRAM... The computers are already in a network with my Netgear router, both of the said computers run the same OS, and that is Kubuntu 8.10 Intrepid Ibex... I think the only missing is the software to turn these computers into nodes in a cluster...

Hopefully, I'll be able to make my own cluster computer and its purpose will be, basically, be a faster computer than my "single" PC right now...

Btw, while I see in the Internet that most people use of a cluster computer is for a "render farm", well, that is just actually part of the main reason why I want to make myself a cluster computer... I actually want to make a cluster computer for "general" use, not just for rendering jobs but also for something like, say, I used to play a game in a single computer which runs at 20 fps, then it'd be running at 30+ fps when I play this game again with my new clustered computer, or like running a heavy application that used to be quite slower in a single computer but should be running smoother and better on a clustered computer... something like that actually.... -_+

I also did some research before I finally decided to ask help from this community, I searched from Google, but since I'm a newbie when it comes to this kind of stuff, I need a more detailed and a rather, more understandable how-to's or instructions vis-a-vis this kind of stuff (i.e. cluster computing)

So uhmmm, anyway, I'll be waiting for your help, tips, or advise... If you have any question, feel free to ask... Thanks in advance... God bless... ^^

~ShadeS_07 -_+ :popcorn:

---

### Post by ShadeS_07 on 2010-03-28
Uh, it was yesterday when I posted this thread and now, it's on the 8th page of "General Help"... I don't usually bump my post, but I'm just worried that people won't be able to see it... My apologies for breaking the netiquette... But anyway, how's thread bumping considered in this community? If I just wait even if my thread has gone through several pages, will it still be seen by others, or is it sometimes necessary to bump my thread? Again, I'm sorry, it's actually my first time to bump a thread of mine in this community... The last time I did such was in another community / internet forum, and I got a temporary ban for doing such... Hehe... 

Peace out yo.. God bless... ^^

~ShadeS_07 -_+ :popcorn:

---

### Post by btmiller on 2010-03-28
Things aren't quite a simple as you make them out to be. Programs have to be specifically written to take advantage of a cluster, or there needs to be some way to divide up the work so that bits and pieces of it can be done on each computer (e.g. on a render farm each computer renders one frame of a movie). There is software like Mosix and similar stuff that will migrate processes between computers, but the individual processes won't run any faster. For example, without specially designed software there's no way to make a game use two video cards on separate machines to achieve more fps. In these cases you're better off buying a better processor or video card (maybe use SLI or CrossFire).

One of the main hurdles to building an efficient cluster is the network. Even 1 gigabit Ethernet is far, far slower than the internal links within your computer that connect the processor, memory, and high-bandwidth perephierals (e.g. PCI express cards). Where I work, we have a cluster for computer simulation, and the network is often the bottleneck for large calculations (this is what makes stuff like render farms attactive, each process is completely separate so they don't need to use the network much; these applications are often called "embarrasingly parallel"). Computer clusters for parallel scientific computing like the one I use often need extremely high-speed and low latency networking (mostly InfiniBand, but 10 gigabit Ethernet is growing in popularity) to run tightly coupled parallel scientific applications.

In summary, if you just want a simple cluster install something like Mosix (I think it's been superseded by another project, maybe kerrighed(?) -- there was a thread floating around here about this at one point, but I don't have the reference handy) and play around with it. If, however, you want games and other application software to run faster that probably won't do it; programs have to be specially written to take advantage of parallelism, or there must be some way to split a large task up into smaller ones efficiently.

---

### Post by ShadeS_07 on 2010-03-29
Wow, thank you very much, btmiller... ^^

So, basically, the thing I said about "general" use is quite impossible for a cluster machine? So far by now, in all the software / applications that I've been using in my PC, only Blender 3D is the only software I know of that could be the thing you're saying as a "specially written program for a cluster machine"... Am I right?

Therefore, does that mean, in my case, the use of a cluster computer would be just for rendering my 3D projects with Blender? So if ever I made myself a cluster computer, it's sole purpose would probably be a "render farm" for rendering 3D projects?

Well, I just thought I could make myself a home made "supercomputer", being adventurous, trying another way to upgrade my computer...

Oh, and not to mention the "Fast Ethernet" I have here... If I made a cluster computer, having nodes being networked through fast Ethernet type of interface, would I be able to make a better computer or a worse one? Hehe... This is interesting...

Thanks again dude, peace out, and God bless always... ^^

~ShadeS_07 -_+ :popcorn:

---

### Post by btmiller on 2010-03-29
You've mostly got it right. To put what I said above in a different way. to really make use of a cluster you need tohave programs designed to run in parallel or programs where you can run many instances at once completely independently (this is the render farm idea). There's not really any way I can think of to take a stock, off-the-shelf game, and tell it to run on two machines (modern games can, however, take advantage of multicore CPUs and stuff like SLI in video cards).

In theory,you can use a cluster for anything but at some point, particularly on a slow network, the cost of communication is going to nullify any advantage you might gain by adding more processors. Google on Amdahl's Law if you're interested in this and you'll quickly see what I mean. Doing rendering is a nice idea because the task is embarrasingly parallel (i.e. very little communication between nodes is required -- NB this does not mean you don't have to think about your network as the compute nodes have to read input and write output from some sort of store). But this doesn't mean clusters are only good at rendering images! Where I work, we use cluster for biomolecular simulation. This does require special software and, to get good efficiency, good hardware.

BTW. the thread I referred to in my first post is [here](http://ubuntuforums.org/showthread.php?t=1030849&highlight=infiniband). You might also want to look at [the Beowulf project page](http://www.beowulf.org) for more info.

---

### Post by ShadeS_07 on 2010-03-30
Thanks again, btmiller... ^^
I appreciate the extra details... :D

But, uhmmmm...

> **btmiller]In theory,you can use a cluster for anything[/QUOTE]

...What does that mean? Or, should I add "...if you have the right software for that 'machine'"?

As far as I know now, concordant to what I've learned so far, a cluster machine would be useless if there's no software that'd be able to run or be designed to run on that machine. So, probably, based on my understanding, if that happens, there would be just a group of machines acting together as one machine, and when I run an ordinary program like, exempli gratia, GIMP (which I believe is an application not designed for a cluster computer...), in a node / a PC, part of the cluster, then it would probably use the resources of that particular machine "only" where I have run that program and will not use any resources from the rest of the nodes within the network that makes up the cluster.

[QUOTE=btmiller]
You might also want to look at the Beowulf project page for more info[/QUOTE]

Actually, I did that before I have created this thread, which have just made me remember that I have a question about it... Hehe... What is Beowulf? Yeah, I've read the FAQ, and it says at the first number:

[QUOTE=Beowulf.org]
1. What's a Beowulf?

Beowulf Clusters are scalable performance clusters based on commodity hardware, on a private system network, with open source software (Linux) infrastructure.

Each consists of a cluster of PCs or workstations dedicated to running high-performance computing tasks. The nodes in the cluster don't sit on people's desks said:**
> 

But, what is it actually? Is it a software, or a community where you can dedicate your PC to be part of their clusters? 

But at the 3rd FAQ it says:

[QUOTE=Beowulf.org]
3. Where can I get the Beowulf software?

There isn't a software package called "Beowulf". There are, however,several pieces of software many people have found useful for building Beowulfs. None of them are essential. They include MPICH, LAM, PVM, the Linux kernel, the channel-bonding patch to the Linux kernel (which lets you 'bond' multiple Ethernet interfaces into a faster 'virtual' Ethernet interface) and the global pid space patch for the Linux kernel (whichlets you see all the processes on your Beowulf with ps, and eliminate them), DIPC (which lets you use sysv shared memory and semaphores and message queues transparently across a cluster). 


So, I think it is not a software... Hmmmm...

Oh, and btw, thanks for that Amdahl's Law reference, I think I've read about it before, or maybe something similar? It says something like 3 PC's, each of which having a 3.0 GHz CPU running in parallel is faster than 9 PC's, each of which having a 1.0 GHz CPU running in parallel... Hehe...

Well, thanks again dude...

God bless and peace out yo... ^^

~ShadeS_07,, -_+ :popcorn:

---

### Post by btmiller on 2010-04-03
Sorry I haven't checked in for a bit. A beowulf is a type of cluster constructed from common off-the-shelf (COTS) parts and using open source software. It's really a class of machines rather than a machine unto itself.

---

### Post by ShadeS_07 on 2010-04-04
Oh, thanks again dude... ^^

Uhmm, hey, check this out... I just found it a while ago...

[http://www.webstreet.com/super_computer.htm](http://www.webstreet.com/super_computer.htm)

It's a pretty useful guide... I read it, and I think that the MPI application is the "special application for cluster computer" you were saying. Hehe... -_+

---

