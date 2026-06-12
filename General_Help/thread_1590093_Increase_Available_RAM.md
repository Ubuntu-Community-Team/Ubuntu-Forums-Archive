---
title: "Increase Available RAM?"
date: 2010-10-07
forum: General Help
---

### Post by csharpplus on 2010-10-07
Hi,

I am an Ubuntu newbie. hope you guys can help with the following:

I have a laptop with 1GB RAM that will be used as a 'computational unit'. I will be accessing it from a different machine (using SSH), and will use it to run a scientific app to crunch numbers (no other apps will be run on it). Given the nature of this app, I will need to have as much free RAM as I can get.

Is there an easy way to configure Ubuntu to consume as less memory as possible by 'giving up' on services I will not be using? (the only thing I will really need is 'SSH server' as I will be accessing this machine using a different computer).

Thanks.

---

### Post by dargaud on 2010-10-07
Two pretty easy replies:
- install more ram, it's cheap.
- don't use ubuntu (sorry folks). If all you need is ssh in text mode, then install a minimalist text-mode Linux. Damn Small Linux for example.

---

### Post by csharpplus on 2010-10-07
Thank you, but it is not easy for me to buy more RAM.

Would you mind helping by telling me what I can do (within ubuntu) to improve the situation?

your help is appreciated.

---

### Post by UnterUn on 2010-10-07
If you must you could do it manually by going to 'system monitor' in  'administration' and forcing applications to quit that are using high  amounts of memory (Make sure its not system crucial). Also if some of  these processes are unimportant or rarely used and start on start up you  could simply prevent them from starting up ('Preferences' >  'Start-up applications')

---

### Post by oldos2er on 2010-10-07
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It sounds like you don't need X (the software that provides a GUI) so that should save you a lot of memory.

---

### Post by mcduck on 2010-10-07
> **oldos2er said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It sounds like you don't need X (the software that provides a GUI) so that should save you a lot of memory.

+1 to this.

Saying that Ubuntu isn't a good choice for low RAM machines is definitely not true. That's just the default everything-works-.out-of-the-box desktop setup. I have a nice Ubuntu machine, installed using the minimal CD, that uses 42MB of RAM *with a graphical desktop*. :D

So, just get the server CD or minimal install CD and set up a CLI system with that. Then add all the additional stuff you need.

Of course it *is* possible to just start with the default desktop setup and then disable/uninstall everything you don't need, and you'll definitely be able to save some resources that way, but if you really don't need most of the stuff included then it sure is easier and less work to start with a minimal setup and only add what you need.

---

### Post by dargaud on 2010-10-07
Yeah, when you remove the GUI, all Linuxes are pretty much equivalent. If it's already installed you can figure out what's running with a combination of "top", "ps" and "sudo service --status-all".

And a brutal solution is to try "sudo aptitude remove xorg" !

And if you want the absolute minimal footprint, do as I do: download BuildRoot and create your own distro that can be fully operational with as little as 4 files (kernel, busybox, uClibc, rcS) !

---

### Post by lukeiamyourfather on 2010-10-07
Agree with what has already been said. Start with the minimal install disc and then install only what you need. If you already have a system running and don't want to install everything again then disable all of the services you don't need and disable the GUI.

---

### Post by csharpplus on 2010-10-07
Hi Guys,

Thank you all for the wonderful advice. I will go ahead and try that.

A couple of questions:

(i) My machine has 1GB of RAM. currently (based on info from 'top') I have about 500MB RAM available. when I look at the 'System Monitor', the total RAM of all the running processes is no more than 100MB.
The question is, where are the 'missing' 400MB?

(ii) also, the system monitor (under resources) 'says' that 220MB are used. this does not match the info from 'top'. who should I believe -- 'top' or the 'resources'?

(iii) Going the 'minimal CD' way, will operations like hard disk read/write (of intense applications) be significantly worse? better? unchanged?

Thanks in advance.

---

### Post by cgroza on 2010-10-07
Those 400 Mb must be cached files because Linux does it so your application will start faster.

---

### Post by Joeb454 on 2010-10-07
> **dargaud said:**
> - don't use ubuntu (sorry folks). If all you need is ssh in text mode, then install a minimalist text-mode Linux. Damn Small Linux for example.

I've seen my website (which runs a wordpress blog) using 80MB of RAM before, that's irssi, apache, mysql & the most bloated blog software going ;)

> **csharpplus said:**
> 
(i) My machine has 1GB of RAM. currently (based on info from 'top') I have about 500MB RAM available. when I look at the 'System Monitor', the total RAM of all the running processes is no more than 100MB.
The question is, where are the 'missing' 400MB?

It's allocated to the currently running processes, such as X (i.e. the graphical display) amongst other things.

> **csharpplus said:**
> (ii) also, the system monitor (under resources) 'says' that 220MB are used. this does not match the info from 'top'. who should I believe -- 'top' or the 'resources'?

I can't really give a definitive answer to this one...
> **csharpplus said:**
> (iii) Going the 'minimal CD' way, will operations like hard disk read/write (of intense applications) be significantly worse? better? unchanged?

It should be unchanged, I'd be surprised if there was any change at all.

---

### Post by csharpplus on 2010-10-07
thanks. 

So now the question becomes, will Linux give these 400MB to a new application that would need them?
Is there a way to tell Linux to 'give' all memory (well, almost all of it) to a new application, assuming this application requires (is in need of) this extra memory?

---

### Post by lukeiamyourfather on 2010-10-07
> **csharpplus said:**
> 
(i) My machine has 1GB of RAM. currently (based on info from 'top') I have about 500MB RAM available. when I look at the 'System Monitor', the total RAM of all the running processes is no more than 100MB.
The question is, where are the 'missing' 400MB?


Probably buffer cache (search for what it is if you don't know), there's also several states of "used" memory and different utilities classify it differently. A default Ubuntu Server install will use about 200MB of memory when freshly booting and nothing else running. You'll be pretty hard pressed to get it much lower than that and still retain basic functionality.

---

### Post by skogs on 2010-10-07
If the system needs the RAM...it will use it.  
If it needs it for your app...you can be assured you'll get it.  Honestly, memory management and the 'reported usage' is not something  you need to worry about with *nix like you did with DOS or Windows.  
It is extremely well thought out, by folks smarter than me.  
[http://librenix.com/?inode=8271](http://librenix.com/?inode=8271)  should also answer why the numbers don't seem to add up sometimes.

If the number crunching that you are doing actually requires more RAM than is available...you will then see the swap rise.  People do not need to worry unless they start filling up swap.

---

### Post by csharpplus on 2010-10-07
skogs,

thank you for your reply.

so basically (if I understand correctly) I will get the 800MB RAM (1GB - the 200MB 'resources' is using) when I need it?  also, say my app really needs 1GB RAM when 800MB is available. what will happen then?

thanks.

---

### Post by lukeiamyourfather on 2010-10-07
> **csharpplus said:**
> 
so basically (if I understand correctly) I will get the 800MB RAM (1GB - the 200MB 'resources' is using) when I need it?


Basically, yeah. Stuff that isn't actively running will get moved into swap on the hard disk if something running needs all the memory.

> **csharpplus said:**
> 
also, say my app really needs 1GB RAM when 800MB is available. what will happen then?


The system will start using swap for actively running processes instead of just sleeping (zombie) ones. This is what they call thrashing and causes severe performance degradation. A problem that fits in the memory and takes an hour to solve might take a week or two or longer to solve if thrashing. The difference between using only memory and thrashing the swap is measured in orders of magnitude.

This is why everyone is recommending more memory because the only way to avoid thrashing is either install more memory or solve problems that require less memory.  If you can share the hardware being used maybe we can suggest what memory to get on a budget. Think of it as a truck, so much stuff is in the truck that it literally can't move. Throwing the spare tire and toolbox overboard will help if on the threshold, but if the load is two or three times greater than what it can haul then you simple need a bigger vehicle (e.g. more memory).

---

### Post by csharpplus on 2010-10-07
Thanks for your help -- it is greatly appreciated.

---

### Post by mcduck on 2010-10-08
> **csharpplus said:**
> Hi Guys,

Thank you all for the wonderful advice. I will go ahead and try that.

A couple of questions:

(i) My machine has 1GB of RAM. currently (based on info from 'top') I have about 500MB RAM available. when I look at the 'System Monitor', the total RAM of all the running processes is no more than 100MB.
The question is, where are the 'missing' 400MB?

(ii) also, the system monitor (under resources) 'says' that 220MB are used. this does not match the info from 'top'. who should I believe -- 'top' or the 'resources'?

(iii) Going the 'minimal CD' way, will operations like hard disk read/write (of intense applications) be significantly worse? better? unchanged?

Thanks in advance.

If you really want to know how your RAM is being used, forget about the System Monitor, instead open a terminal and run "free -m". Then read from the second line, the one that starts with "-/+ buffers/cache". That tells you how much RAM your system and programs are using, and how much is available to them.

The rest of the RAM that shows as "used" is used for buffers (for example things that are waiting to be written to hard drive) and cache (Linux uses all RAM that isn't used for anything else to keep recently used data in RAM. That way it doesn't need to read it from hard drive if you need it again, which greatly improves performance. Reading from hard drive is extremely slow thing to do from a computer's point of view. Since the caching is just something "extra", it still counts as free RAM for programs to use. If a program needs more memory, some cached data is dropped immediately to free some RAM.)

Here's an example:
```

mcduck@Aether:~$ free -m
             total     used     free     shared     buffers     cached
Mem:           497      122      375          0          17         62
-/+ buffers/cache:       41      456
Swap:          397        0      397
mcduck@Aether:~$
```
Here my system and programs are using a total of 41 MB of RAM, with 456MB still available for them if they need it. There's currently 17MB of buffered data, and 62MB is used as cache. Over time the cache will grow to fill most of the RAM that isn't used by system or applications (better use that RAM for *something*, just having it there without doing anything would be pointless ;))

---

### Post by csharpplus on 2010-10-08
mcduck,
 
thanks you. this has been extremely helpful! now everything matches...

---

### Post by dargaud on 2010-10-08
Be absolutely sure that your process doesn't need more than 800Mb of RAM, otherwise don't bother, like others have said. Also when doing intensive computation, consider that the benefit of using older hardware is almost nill: it takes longer and uses more power than a more recent system. Something that would take a week on your optimized but old 1Gb mem / 1 GHz single CPU laptop would take half a day on your recent quad core, while running in the background with all your personal apps on top. It's not for nothing that in scientific computing the systems are changed almost every year.

---

### Post by csharpplus on 2010-10-10
thanks for the helpful advice.

---

