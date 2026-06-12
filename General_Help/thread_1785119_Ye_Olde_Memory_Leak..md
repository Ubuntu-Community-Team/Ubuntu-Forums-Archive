---
title: "Ye Olde Memory Leak."
date: 2011-06-17
forum: General Help
---

### Post by jerome1232 on 2011-06-17
So *something* is taking up ridiculous amount of memory over time on my computer.

Based on this (screenie of system-monitor) I think it's compiz, so what do I do now? Has anyone else seen this?

my release info is in second screenshot, Usually i'd write it down but meh screenshot was more fun.

---

### Post by crispy_420 on 2011-06-18
Try running with out compiz for a little while as you would normally and then compare. From the screenshot I can't see what you are talking about.

---

### Post by jerome1232 on 2011-06-18
Compiz is taking 2.5 GB's of Ram in that screenshot, I just got an update to compiz so I'm waiting to see if it has fixed or not, but ram use has been slowly creeping up since I started up earlier today, compiz is slowly creeping up the list of processes using the most memory.

If i kill compiz ram use immediately drops back down to normal levels.

---

### Post by 3rdalbum on 2011-06-18
```
ubuntu-bug compiz
```

You should report it. It might be related to Unity because Unity runs as part of Compiz. That's incredibly high memory use for Compiz, even with Unity.

The good news is it should be temporarily fixed by simply logging out and logging back in again. Also I believe there are some new Unity updates coming soon, so keep an eye out for those.

---

### Post by cracker89 on 2011-06-18
Well, Im on 10.04... and sometimes compiz does go mad that way.. Reported t as a bug. Memory leaks have hugely to do with your graphic crd drivers... slight details would be helpful... please post them.

running this command every so often
```
compiz --replace  
```
helps alleviate the problem for a while. 

If you are indeed using nvidia, updating to the latest drivers should alleviate the peoblem for good. Worked for me..

---

### Post by jerome1232 on 2011-06-18
I'm using nvidia driver version 270.41.06, I see on nvidia's site they have version 275.09.07.
I do see on it's list of improvements "Improved performance of certain memory allocations." So it may be the ticket.

My card is a GTS 450.

It takes about a day for the ram to fill up so I am waiting to see if the compiz update I received fixed the issue or not, if it does not I will try the newer driver (how I hate using their installer though)

I'll update when I do that, might take me a bit I work 3 12 hour shifts over the next 3 days so I won't have much time. Thanks for the input.

If a driver update fixes it, then it's not a bug in compiz and I wouldn't report it as such correct?

---

### Post by doas777 on 2011-06-18
just out of curisoity, can you confirm your readout with 
```

free -m

```
after subtracting out your cache?

---

### Post by jerome1232 on 2011-06-18
I have killed it since then so ram isn't high yet (it takes awhile to creep up and I'm currently waiting to see if it has been fixed) but yes I ran free and I recall having slightly less than 3.1 GB's used, with about 800 MB in cache. That was with no user applications running.

edit: Also if you look at my screenshots, in the top right I have a system-monitor, the dark green is ram used - buffers/cache. You can see in those pictures how full it is.

Currently after 7 hours of being ran, it's (compiz) is using an understandable 119 MB's of ram. It took *AWHILE* the past couple of times to get to that ridiculous amount mentioned earlier. (programs would begin to refuse to start due to lack of memory after about a day)

---

### Post by cracker89 on 2011-06-18
> **jerome1232 said:**
> 
1. It takes about a day for the ram to fill up so I am waiting to see if the compiz update I received fixed the issue or not, if it does not I will try the newer driver (how I hate using their installer though)
Try [Envy]("http://albertomilone.com/nvidia_scripts1.html"). Its a good piece of work. Pretty much effortless, it even takes care of the old driver for u.

> **jerome1232 said:**
> 
2. If a driver update fixes it, then it's not a bug in compiz and I wouldn't report it as such correct?

Umm.. wait a bit and see. A bug's a bug.

---

### Post by jerome1232 on 2011-06-20
Okay so envy doesn't support higher than 10.04, so I installed it (the nvidia driver) the manual way. Compiz seems to be staying under control (using 218 MB's or ram atm) I'll keep an eye out on it. Thanks for the tips so far.

---

### Post by cracker89 on 2011-06-20
Ooh yes. Didn't take that into account. I'm still hooked on lucid :P

Cheers. Hope it works out for you. :)

---

### Post by mcellius on 2011-06-20
Are you running the multiload indicator?  I was having the exact same problem as you describe, and at the suggestion of someone else I got rid of the multiload indicator (quit it and uninstalled it), rebooted, and the problem has never returned.

However, I also found another recommendation (by someone named Uri Herrera, in the Ask Ubuntu forums) and tried it, too, so this might have been what fixed it.  He wrote:

Add this to your repositories.
       deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main #xorg-edgers PPA          deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main #xorg-edgers PPA   and then
       sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542       sudo apt-get update       sudo apt-get dist-upgrade   see if it helps.


-----


Whichever of these things worked, I can't say, but as I said the problem hasn't returned.  (And I'm pretty new to Linux and Ubuntu, so I can't really assure anyone that the second suggestion might not be dangerous in other ways, but so far I haven't encountered any problems.)

---

### Post by jerome1232 on 2011-06-23
> **mcellius said:**
> Are you running the multiload indicator?  I was having the exact same problem as you describe, and at the suggestion of someone else I got rid of the multiload indicator (quit it and uninstalled it), rebooted, and the problem has never returned.


Yes I am, and it appears after updateing the nvidia driver I now longer have a memory leak, but still after a day or so of running, apps will refuse to launch and I noticed, due to that load indicator, that my iowait on the cpu time maxes out and then my computer hard locks shortly after that. This is not a new problem, just one I thought was being caused by the memory leak.

I'm not sure how to get any relevant data to figure it out either. :S

In the interim I have removed that multi-load indicator from my startup list to see if that stops the misbehavior. (I miss it already!)

---

