---
title: "I can't figure out what is using my RAM (and it's not the cache)"
date: 2010-06-15
forum: General Help
---

### Post by Kostya on 2010-06-15
Hi,

I've been troubled by the high amount of RAM that is used by my Ubuntu desktop. Before I installed Ubuntu 10.04 (desktop, 64-bit) my system used around 500MB of RAM when no applications were open (just cold boot into the GNOME under 9.10). But when I installed Lucid, I've noticed that my used memory is now reported as 1GB or more as soon as I log into the system.

I want to figure out what is using all the extra RAM but I can't seems to find the culprit. I looked at all of the processes and numbers just don't add up. I exported the list of processes into a file and summed up the memory used by every process in a spreadsheet. The total came to around 700MB. Yet, both System Monitor and "free" reported the time that system was using over 1GB of memory. This means that at least 300MB of RAM are used but not by any process, at least as reported by "ps". 

Does anyone have any ideas what might be going on here?

Thank you in advance.

---

### Post by ubunterooster on 2010-06-15
That is memory standing ready to be used; the more memory you have the more is in "standby" I have over 1.5GB in standby and found that this is being done to increase performance :D

So, yes, it does not add up because some (system monitor) count this RAM as free while others (ps) see it as used

---

### Post by Kostya on 2010-06-15
Thank you for your quick reply. I've never heard of "standby memory" in linux. When I google for it only Windows 7 related conversations come up. Do you know of any place I can find more information about it?

Thank you.

---

### Post by Kostya on 2010-06-15
In addition to the above I have a laptop with 3GB of RAM and freshly installed Lucid on it and it only shows about 300MB as used. So I am not seeing the same behavior on another machine which is basically configured the same way (although I am sure hardware is different).

---

### Post by ubunterooster on 2010-06-15
LOL, see: [http://www.linuxatemyram.com](http://www.linuxatemyram.com)
near the end is a link for more info

Why it acts differently on different computers I do not know.

---

### Post by Kostya on 2010-06-15
I've seen this page. Unfortunately, this is not what I am talking about. I know cache is taking a lot of space in RAM and I am not worrying about it. When I run "free -m" I get this right now (I have a few apps open):

```
             total       used       free     shared    buffers     cached
Mem:          **3836**       2175       1660          0        176        630
-/+ buffers/cache:       1368       **2467**
Swap:         2047          0       2047
```

Out of 3.7GB of RAM total I have about 2.4GB free. This means I have about 1.3GB used. When I close every app (or just boot) the number is 1.1GB. Cache takes another 1.5GB or so and I don't really care about that. I want to know what is using 1.3GB of RAM when the total memory used by all of the processes is only 700MB.

---

### Post by Kostya on 2010-06-16
Any other ideas? Anyone?

---

### Post by dtfinch on 2010-06-16
Did you make sure to show all processes, not just those running under your user name?

---

### Post by Kostya on 2010-06-16
Yes, I ran "ps -Ao rss,cmd" to get the list of all the processes and their memory utilization. This problem is driving me crazy because I don't understand what's going on with the system. I experience some sluggishness occasionally and I wonder if this is related, but I can't seem to solve it.

---

### Post by Kostya on 2010-06-16
Well, I was trying to solve this for weeks. I've just rebooted the system and the issues seems to be gone. I logged in and my memory usage without any apps open is about 450MB which is what I would expect. 

There were quite a few updates installed yesterday and today. I guess somebody fixed something somewhere... :-) I would love to know what it was but I guess it will remain a mystery. There were fixes to fglrx and xserver. Perhaps, there was some problem with ATI proprietary driver or something. There were also many fixes to Evolution and related libraries. 

In any case, I hope it stays fixed. :-)

Thank you all.

---

### Post by acid303 on 2010-06-17
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988")
In terminal, run 'glxinfo' command or invoke 'glxgears' to release the 'uncleared' memory. You might need 'mesa-utils' package installed.
 - Create a bash script to run at start up
   #!/bin/sh
   while [ 1 ]
   do
     glxinfo
     sleep 60
   done

---

### Post by Kostya on 2010-06-18
Thank you for the info. Interestingly enough, it looks like I do have a memory leak now. I didn't before the updates. My memory usage keeps creeping up ever so slightly over time. However, I am not using Compiz and running the code suggested doesn't seem to change anything. So they fixed one thing but broke something else... *sigh*

---

