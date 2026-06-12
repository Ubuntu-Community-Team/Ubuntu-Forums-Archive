---
title: "So much memory is being used!"
date: 2009-06-29
forum: General Help
---

### Post by javaTN on 2009-06-29
Hi all,
Im in quite a bit of a dilemma here. Last time i checked, I heard Linux was a better operating system because it uses less system resources, which makes it capable of doing more. I can vow to that statement having put it on many computers that can barely run windows... however, on my main desktop system that I am currently typing this on, Ubuntu 9.04 seems to use quadruple the amount of memory my Windows XP install normally used.

For example... right now its using 808.5 MB (or ~82%) of my total memory which is 1 GB. On windows XP, while simply running firefox and the operating system, it uses roughly 250 MB (~23%).

Can someone please explain to me what is going on here? I dont think I should have to purchase MORE memory to enjoy what i normally do on Windows XP.

Tom

---

### Post by Slim Odds on 2009-06-29
How are you measuring this?

People get constantly confused about memory usage.

For one thing, unused memory is useless. It might as well be used for something.

There are different ways memory is used. For programs and for cache.

---

### Post by javaTN on 2009-06-29
I am measuring this with the System Monitor tool found in the Administration menu.

I know lots of memory is being used also because program responsiveness immediately drops down and animations are slowed down and choppy.

Also, when I run VirtualBox for instance, the audio in the virtual machine is also choppy.

---

### Post by mikewhatever on 2009-06-29
Which program is using the most memory then?

---

### Post by credobyte on 2009-06-29
Terminal ( show the output ) :
```
top
```

---

### Post by ericab on 2009-06-29
1 gb of ram #1 really isnt adequate for daily usage. (for a desktop gui)
2, running virtualbox uses as much ram as you pre-allocate in the instance of OS you are running.
advice, slap in another 1gb stick
what amount of ram is used RIGHT after you system boots into your desktop ?

---

### Post by mikewhatever on 2009-06-29
> **ericab said:**
> 1 gb of ram #1 really isnt adequate for daily usage. (for a desktop gui)
...

It depends on what you do with the system, but in my experience it's not true. My full Ubuntu installation with compiz and a couple of programs users under 300 MB of RAM.

---

### Post by javaTN on 2009-06-29
> **mikewhatever said:**
> Which program is using the most memory then?

anddddd the output of top is:

```
Tasks: 125 total,   1 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s): 39.5%us,  8.0%sy,  0.2%ni, 51.3%id,  0.4%wa,  0.5%hi,  0.1%si,  0.0%st
Mem:   1011432k total,   999500k used,    11932k free,    13720k buffers
Swap:  2963952k total,   192008k used,  2771944k free,   167552k cached

```

That is with Firefox running, obviously the OS, and the terminal window (which the terminal shouldnt have a significant impact in this test).

And from a basic math problem, Whoa... that calculates to 98% of memory being used? Eak?

---

### Post by dmizer on 2009-06-30
While running top, hit <shift>+f and select "n" and hit <enter> so that the list is ordered according to memory use. What is at the top of the list?

Also note, when running VirtualBox, the virtual machine's memory is subtracted from your physical memory. So if you have your virtual machine set to use 512 meg, you'll only have 512 meg left for your physical machine.

I would hardly call 1gig "insufficient" for desktop use, but it's probably not enough for working with virtual machines.

---

### Post by javaTN on 2009-06-30
oh wow i did not know it used it like that... but anyways, it seems that Firefox is being the memory hog.. and its always that i have firefox running.. now, how can I either get firefox to use less memory, or whats a better browser that doesnt horde all my RAM? (its hard to say better browser, because ive been using it for ever!)

here is the output of top with it sorted by memory:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4214 tom       20   0 1074m 411m  17m S  2.3 41.7  79:33.89 firefox            
 3057 root      20   0  236m  73m 7332 S  0.3  7.4  50:51.70 Xorg               
22890 tom       20   0  661m  46m 5636 S  0.0  4.8  18:06.37 totem              
 7898 tom       20   0  120m  19m  12m S  0.7  2.0   0:21.51 npviewer.bin       
 3565 tom       20   0  363m  17m 8104 S  0.0  1.7   0:07.33 gnome-panel  
```

thoughts?

---

### Post by ManiacDan on 2009-06-30
Firefox is quite a memory hog to begin with, and yours seems to be using more than most.  You could try to switch to epiphany or another browser that doesn't use so much RAM.

It's also a good idea to buy more memory.  I have 2GB in this machine, though I use a lot more programs than you.

-Dan

My TOP, for reference:
```
Tasks: 193 total,   4 running, 189 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.3%us,  8.3%sy,  0.2%ni, 65.5%id,  1.1%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2059640k total,  1945904k used,   113736k free,    11220k buffers
Swap:  4192956k total,   286756k used,  3906200k free,   145668k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                           
 5091 me        20   0 1260m 540m  36m R    4 26.9 420:50.85 firefox                                                                                                                                           
 5827 me        20   0 1246m 335m 9424 S    0 16.7 118:15.02 ZendStudio                                                                                                                                        
 5407 me        20   0  385m 298m  29m S    8 14.8 379:16.48 VirtualBox                                                                                                                                        
17692 me        20   0  424m 146m  21m R    5  7.3  64:31.29 epiphany-browse                                                                                                                                   
 4241 root      20   0  475m 134m  20m S   20  6.7 367:14.63 Xorg                                                                                                                                              
 4852 me        20   0 89540  64m 3060 S    0  3.2   1:12.07 notify-osd                                                                                                                                        
 5070 me        20   0  136m  60m  10m S    2  3.0 100:02.63 pidgin              
```

---

### Post by t4thfavor on 2009-06-30
I restart ff now and then to combat that. I also compiled 3.5 b4 from source, and it seems to help. Though I do have 4gb on my play desktop, and 8gb on my workstation...

---

### Post by dmizer on 2009-06-30
What add-ons do you have enabled on Firefox?

---

### Post by javaTN on 2009-06-30
> **dmizer said:**
> What add-ons do you have enabled on Firefox?

right now the only "addons" enabled in my firefox are:
a mac4lin aqua theme, adobe reader plugin, quicktime plugin, shockwave flash plugin... thats basically it (i didnt really add any special).

the issue too is that, it seems newer memory is MUCH cheaper than old memory. ive had my current desktop for 5 years, and it has DDR 400 memory in it.

for 2 GB it will cost me close to $80. while, if i purchased DDR2 (which my computer cant run, but just for price comparison)... it would cost $40 for 4 GB. so unfair!

---

### Post by t4thfavor on 2009-06-30
memory seems to follow the same supply and demand as everything. When PC's are new, the supply is very high, and the demand is not so high (OEM's and system builders) as PC's get older manufacturers slow production of memory, and more people are then ready to upgrade hence the demand. This means you will be screwed when you try to upgrade. I follow the philosiphy of Fill your mobo when you get it new because it won't be worth it when its old. I probably save money by having the extra memory in the long run since stuff happens much faster.


The day I bought my quad I put 8GB (200USD total) in it and I have never been disapointed.

---

### Post by Slim Odds on 2009-06-30
> **t4thfavor said:**
> The day I bought my quad I put 8GB (200USD total) in it and I have never been disapointed.

+5

Couldn't agree more....

---

### Post by kmg90 on 2009-06-30
I just put 2 gb DDR2 RAM dual-kit in my old 8400 Dell and it only was 23 bucks

---

### Post by ericab on 2009-06-30
add another GB of ram, and also download firefox 3.5 just released today

---

### Post by bodhi.zazen on 2009-06-30
first, memory management if very different between Windows and Linux so you can NOT blindly apply your windows knowledge to Linux.

See :

 [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

Second, most desktop users will not need more then 1-2 Gb RAM MAX. you will need more if you perform RAM intense applications such as virtualization.

For the vast majority of uses, the idea that you need more then 2 Gb is simply untrue.

---

### Post by t4thfavor on 2009-06-30
Not that we need it, but we really really want it!


You may not need it, but I swear you can tell a difference.

---

### Post by Slim Odds on 2009-06-30
I know that this post will be off topic, but a message to the system administrators.

Why does this thread show 19 replies but 0 views?

Clearly does not make sense.

---

### Post by ManiacDan on 2009-06-30
I agree up to a point.  Most normal, non-IT professionals will not need more than 2GB of ram for the next few years, especially in linux.  However, for a developer like myself, it's not uncommon to be using:
firefox (1gb of ram, minimum)
zend (java program, enormous memory footprint, currently using 600mb)
SQL Developer (java again, for oracle databases.  400mb currently)

Even without virtualization, that's 3 programs using 2gb by themselves.  then you have the OS, terminals, and chat clients, each of which have prodigious scrollback buffers.  It's a lot of data.

-Dan

---

### Post by bodhi.zazen on 2009-06-30
output of 

```
free -m
``` ;)

1 Gb for firefox is huge, well beyond "normal" usage. I have just over 100 tabs open (112 to be exact) am am using 312 Mb for firefox.

---

### Post by michy99 on 2009-06-30
> **bodhi.zazen said:**
> I have just over 100 tabs open (112 to be exact) am am using 312 Mb for firefox.

I just have to ask. Is this for testing purposes, or is this a usual occurrence for you? If I open more than ten, I start to loose track.

---

### Post by itsjareds on 2009-06-30
I have only 1GB of RAM as well, and I never use more than 500MB of it, except maybe a bit more if using Virtualbox. I'm a developer but I am more comfortable with a text editor.. so no high memory usage programs there.

I even created a 1.5GB swap partition when I installed Ubuntu, and every time I checked the system monitor it would tell me 0kb is being used. Last night I just decreased this from 1.5GB to 300KB.. still 0kb is being used but I like to keep safe.

Firefox usually stays at about 100MB while I'm using it.. I don't know where these numbers of 1GB from firefox are coming into play. I usually have one or two windows of 6 tabs each open.

---

### Post by Slim Odds on 2009-06-30
> **michy99 said:**
> I just have to ask. Is this for testing purposes, or is this a usual occurrence for you? If I open more than ten, I start to loose track.

LOL, I was going to ask how many months it took to open all those tabs......

---

### Post by bodhi.zazen on 2009-06-30
> **michy99 said:**
> I just have to ask. Is this for testing purposes, or is this a usual occurrence for you? If I open more than ten, I start to loose track.

No, 100 + tabs is actually fairly routine for me. When I get to over 100 I try to cut down.

When I IRC I may have 40-50 channels as well, although I recently cut back on that too :lolflag:

---

### Post by dmizer on 2009-06-30
> **javaTN said:**
> right now the only "addons" enabled in my firefox are:
a mac4lin aqua theme, adobe reader plugin, quicktime plugin, shockwave flash plugin... thats basically it (i didnt really add any special).

I don't think more memory will solve your problem. Your Firefox is certainly eating too much memory. I suggest disabling/uninstalling each of those addons/plugins one by one and trying firefox to see if memory usage is still high. If you disable a plugin and memory usage drops significantly, you'll know what the problem is. I suspect your problem is either the mac4lin theme or the adobe reader plugin.

---

### Post by dmizer on 2009-06-30
> **Slim Odds said:**
> Why does this thread show 19 replies but 0 views?

It shows 27 replies and 28 views for me. Is it still happening? If not, try refreshing and/or dumping cookies.

---

### Post by gradinaruvasile on 2009-06-30
The memory usage itself shouldnt be a problem. Firefox uses memory like crazy with flash content web pages, try using another browser (like chrome or midori) for pages without flash.
I have on the work desktop an uptime of 50 days i think and i ran everything from games to virtual machines on it - it has 2 GB RAM on it and typically i have 100-200 MB free mem reported everytime i look.

---

### Post by earthpigg on 2009-06-30
> **bodhi.zazen said:**
> No, 100 + tabs is actually fairly routine for me. When I get to over 100 I try to cut down.

When I IRC I may have 40-50 channels as well, although I recently cut back on that too :lolflag:

what, pray tell, are in these 100ish tabs you routinely have open?

---

### Post by javaTN on 2009-06-30
most amount of tabs I have had open while running Windows was 25. its just a habit for me to open every link in a new window to stay organized and not have to use the back button in my history.

right now after a days use of firefox, its up to 59% ram usage... i have 12 tabs open.
i also have a habit of closing firefox with tabs in it because I hate to exit the app and then forget where I last was.

---

