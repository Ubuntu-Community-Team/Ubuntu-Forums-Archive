---
title: "Linux is obsolete ...."
date: 2006-06-25
forum: General Help
---

### Post by el_rata on 2006-06-25
This is a mail conversation between Linus Torvalds and Andy Tanenbaum. It's very good.

[http://xratx.blogspot.com/](http://xratx.blogspot.com/)

Enjoy.

---

### Post by Ctrl+Alt+Del on 2006-06-25
ehhrm, this conversation took place in 1992... It's kind of ..old

---

### Post by el_rata on 2006-06-25
just passing the knowledge ...

---

### Post by userundefine on 2006-06-25
Yeah, most people know about the rivalry.  And we also know who was proved right in the long run.

---

### Post by az on 2006-06-25
A very nice read.

Microkernel versus Monolythic refers to the fact that linux is one-big-chunka code and that's why you would need to compile an extra kernel module for it for a video driver or vmware or something - there is no binary interface that stay the same between kernel versions.  It is a lot easier to write (and collaborate in a free and open way) that way, which is sort of why the GNU kernel (the hurd) is still not ready to go.

---

### Post by kaveraj on 2006-06-29
The debate has been renewed as of May 2006

You can read more about it here
[http://www.coyotos.org/docs/misc/linus-rebuttal.html](http://www.coyotos.org/docs/misc/linus-rebuttal.html)

Article from IEEE magazine by Tanenbaum listing the advantages of microkernel. 
[http://www.computer.org/portal/site/computer/menuitem.5d61c1d591162e4b0ef1bd108bcd45f3/index.jsp?&pName=computer_level1_article&TheCat=1005&path=computer/homepage/0506&file=cover1.xml&xsl=article.xsl&](http://www.computer.org/portal/site/computer/menuitem.5d61c1d591162e4b0ef1bd108bcd45f3/index.jsp?&pName=computer_level1_article&TheCat=1005&path=computer/homepage/0506&file=cover1.xml&xsl=article.xsl&)
Afer reading this I agree more with him than linus.. Previously it was other way around. Maybe Linus is too old to learn new tricks of the trade..

---

### Post by jgcamp99 on 2006-06-29
If I understand what this guy is advocating, he seems to think decentralization is superior to centralization ? So if his statement of this is true:

"Current operating systems have two characteristics that make them unreliable and insecure: They are huge and they have very poor fault isolation. The Linux kernel has more than 2.5 million lines of code; the Windows XP kernel is more than twice as large.

One study of software reliability showed that code contains between six and 16 bugs per 1,000 lines of executable code, (1) while another study put the fault density at two to 75 bugs per 1,000 lines of executable code, (2) depending on module size. Using a conservative estimate of six bugs per 1,000 lines of code, the Linux kernel probably has something like 15,000 bugs; Windows XP has at least double that.

To make matters worse, typically, about 70 percent of the operating system consists of device drivers, which have error rates three to seven times higher than ordinary code, (3) so the bug counts cited above are probably gross underestimates. Clearly, finding and correcting all these bugs is simply not feasible; furthermore, bug fixes frequently introduce new bugs.

The large size of current operating systems means that no one person can understand the whole thing. Clearly, it is difficult to engineer a system well when nobody really understands it.

This brings us to the second issue: fault isolation. No single person understands everything about how an aircraft carrier works either, but the subsystems on an aircraft carrier are well isolated. A problem with a clogged toilet cannot affect the missile-launching subsystem.

Operating systems do not have this kind of isolation between components. A modern operating system contains hundreds or thousands of procedures linked together as a single binary program running in kernel mode. Every single one of the millions of lines of kernel code can overwrite key data structures that an unrelated component uses, crashing the system in ways difficult to detect. In addition, if a virus or worm infects one kernel procedure, there is no way to keep it from rapidly spreading to others and taking control of the entire machine.

Going back to our ship analogy, modern ships have multiple compartments within the hull; if one compartment springs a leak, only that one is flooded, not the entire hull. Current operating systems are like ships before compartmentalization was invented: Every leak can sink the ship.

Fortunately, the situation is not hopeless. Researchers are endeavoring to produce more reliable operating systems. Here we address four different approaches that researchers are using to make future operating systems more reliable and secure, proceeding from the least radical to the most radical solution."

This microkernel concept would have to achieve the same darn thing only be spread out over several files, which is probably where Windows is going and why there is twice as many lines of code and estimated bugs. So now he thinks spreading it out all over the place is the way to go. And please, cell phones secure. I have no doubt President Bush isn't already using methods to record those type of conversations.

I don't know nearly as much about OS and kernels that AT or LT know, but sometimes the hardware drives the software and sometimes it's the other way around too. Centralized or Decentralized kernel, it still has to interface with the rest of it. AT says it himself:

"The large size of current operating systems means that no one person can understand the whole thing. Clearly, it is difficult to engineer a system well when nobody really understands it."

That statement in and of itself should refute his contention that he even knows what he's talking about, he's one person, how does he even understand the whole thing ? I guess what I'm really asking is, if there are that many bugs per 1,000 lines of code, why does AT seem to think or contend that breaking this code up into a plethera of files is better than having it all in one place in sections of the kernel's code ? The error/bug rate doesn't change just because that chunk of code was moved to a separate file. People make errors, some inadvertant, others intentional. One might have to ask, Is this bug really an intentional unlocked back door in case something goes awry for a fix (positive outlook) or whether the programmer is disgruntled (negative outlook) ?

---

### Post by jgcamp99 on 2006-06-29
"This brings us to the second issue: fault isolation. No single person understands everything about how an aircraft carrier works either, but the subsystems on an aircraft carrier are well isolated. A problem with a clogged toilet cannot affect the missile-launching subsystem."

BTW, this was the dumbest analogy I've ever heard. One would assume even with AT's decentralized modular OS theory that all the modules linked would have some relevance as to why it was linked to the kernel in the first place. So saying something like a clogged sewage system not effecting the missile launching system is stupid on an aircraft carrier. Yes, it would be nice if every aspect was compartmentalized, your socks and underwear had it's own drawer, but sometimes, you have to put your socks and underwear in the same drawer. AT should know this, unless he doesn't fold and put away his own laundry. It's a common problem, not the end of the world. AT takes the easy way out on this, it's easy to rip Windows, even Linux, but really to compare cellular phones and tvs to computers. OS's have to be more complex simply bacause of the power and capability involved.

---

### Post by nocturn on 2006-06-29
[QUOTE=jgcamp99]
That statement in and of itself should refute his contention that he even knows what he's talking about, he's one person, how does he even understand the whole thing ? I guess what I'm really asking is, if there are that many bugs per 1,000 lines of code, why does AT seem to think or contend that breaking this code up into a plethera of files is better than having it all in one place in sections of the kernel's code ? The error/bug rate doesn't change just because that chunk of code was moved to a separate file. People make errors, some inadvertant, others intentional. One might have to ask, Is this bug really an intentional unlocked back door in case something goes awry for a fix (positive outlook) or whether the programmer is disgruntled (negative outlook) ?[/QUOTE]

AT is quite correct in his assumption.  In his example when using a microkernel, only 4000 lines of code compose the actual kernel.  

All the other code resides outside kernel space.  A compromise of a device driver does not result in a compromised kernel, in fact, the intruder will not even be able to access data belonging to other drivers.

A lot of Linux/Unix developers agree with his assumption without realizing it.  You can see this happening in code that uses privilege seperation (SSH being a case in point) or things like userspace filesystems.  
If both are a good idea, why should a microkernel be any different?

---

### Post by jgcamp99 on 2006-06-29
"In his example when using a microkernel, only 4000 lines of code compose the actual kernel."

Again, there is 4,000 lines of code, how does that improve the bug rate. AT quotes 2 studies that put bug rates between 2 and 75 per 1,000 lines of code. Poor code is poor code. And in the end, whether it be a small kernel with satellite files that interface with them, it all has to wind up doing the same thing anyway as a complete system of kernel and files. The code has got to be written elsewhere, just as it is in one larger kernel and smaller satellite files. I wonder why cpu's are going to multi-core, with on-chip memory controllers as opposed to older way of doing it, a dedicated cpu and a more diverse motherboard chipsets and pipelines of inefficiency. Some of the integrated cpu's, theoretical pictures show these things as getting ridiculously large. For me, the software code has to be similar in terms of complexity. One has to pass/hand off the necessary lines of code at a certain point to another module or file in a decentralized scheme. It has to be an ideal that the code is as efficient as it's going to be when it's written in the first place, nobody like superfluous code. I think the differences between Windows and Linux shows us what a certain amount of decentralization does, it requires more code in the kernel to look at other places to hand that task off, it requires even more processes for the cpu to manage and handle. Holding up a cell phone and saying this works better than Windows or Linux is ridiculous, I don't know of a single cell phone that can do what a desktop, much less a notebook can do. Let's face it, theoretically you could put OS X on an iPod, but would it be as powerful as a Powerbook or a PowerMac ? Both hardware and software limitations. AT's OS theories are all based on everything/all else being equal, and that's not the case. Bottlenecks in PC's exist because hdd's are the slowest things in the system. And so it is with code. Complex SQL queries in databases illustrate this. Anything I do, I try to do modularly, in chunks so that something like MS Access can handle it without choking. Whatever it is, in the end one has to do so much and hand it off to another for further processing. And yes, I've seen others do it more efficiently with SQL too, but the single query they do it with, is like Linux or Windows it's much larger and more complex as opposed to having a query do one thing and then using another query to process/further refine the results of the first query. It takes both about as long to run though and in the end, the source tables all need to be processed, same number of records and relational data.

---

