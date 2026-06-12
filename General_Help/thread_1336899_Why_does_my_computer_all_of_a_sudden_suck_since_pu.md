---
title: "Why does my computer all of a sudden suck since putting ubuntu on it?"
date: 2009-11-25
forum: General Help
---

### Post by Lu Seraph on 2009-11-25
Ok this has NEVER happened to me before. Never before have I experienced something so horridly slow or annoying in my life. 

I've had Ubuntu installed before on pentium 2 unites that ran WAY faster than this and I just don't get what's wrong.

I'm using an old celeron p4 but this is just retarded, everything runs in snail mode and it's running slower than it used to on this computer.

Some of the issues I have are VERY slow start up times, Very slow to open up my programs (any and all) I click on something and wait at least a minute before it actually opens and when it does there's 10 of em because I figure gee it's been 25 seconds I might not have clicked it...so I double click and ten of them pop open a few minutes later. 

Like my external hard drive today. I clicked on it maybe twice, then I right clicked and selected "browse folder" finally it opens. OVER 100 TIMES.

It took me seriously 5 minutes to close them all. 

Sound USED TO work on  Ubuntu before I reinstalled it over top of windows/ubuntu partitions. 
No more sound. 

Also I've tried using world of warcraft the same files as I had on my ubuntu pc ages ago and I can't even log in because it's THAT slow. I've run WoW x4 on a p3 with No Lag. What is going on with this machine?

I can't even play bejeweled on it because it lags that bad. I normally score over 100k in under a minute on the facebook app but now I can't even manage a 30k score with all the lag.

Oh and when I'm typing (I type pretty fast) the computer types at about 10 wpm and I have to go stretch and walk around while I wait for it to finish the paragraph I've typed out (which takes about 3 mins for 5 mins of typing to come up) so I actually can't even write on here without waiting a while for it to show up!

 This bytes.

Help!

---

### Post by fluffman86 on 2009-11-25
Did you set up a swap partition?  

How much RAM do you have?

Have you run a memtest to make sure that your RAM is good?

Do the programs (esp the typing) run this slow from the LiveCD?

---

### Post by Lu Seraph on 2009-11-25
After clicking reply ten times...gah...my updater is running and it takes about 10  mins to check for updates.
My system monitor says 
456.8MB memory 
Celeron 1.80
I'm only using about 317MB of ram on average, but my processor is stressed to the max. 


I never had any of these issues with my wubi install of ubuntu ever.  It ran slick and fast that's why I didn't fix my windows when I got locked out of it. (I didn't have the code  to activate windows)

---

### Post by fluffman86 on 2009-11-25
First problem? It's a Celeron.  :P  Haha, those were terrible processors.  

Oh, anyway.  In system monitor, does it list swap?  How much are you using?  how much do you have?

While you're there, flip over to the file systems tab.  What does it list for "type" next to "/"?  It should be ext4...

---

### Post by jacobs444 on 2009-11-25
what version are you using, if 9.10, then you may need to use the LTS as ubuntu, and most distros as a rule get slower for every distro you upgrade to. This is because the kernel gets bigger to support newer hardware and options.

---

### Post by jocko on 2009-11-25
> **jacobs444 said:**
> what version are you using, if 9.10, then you may need to use the LTS as ubuntu, and most distros as a rule get slower for every distro you upgrade to. This is because the kernel gets bigger to support newer hardware and options.
That's just nonsense. Even if the kernel would get a little bit bigger with each release, it would not affect the performance of the distro in any noticeable way. The karmic kernel (the /boot/vmlinuz file) is just 3.7 Mb, add to this the modules that needs to be loaded on different hardware and I bet you are still below a 10 Mb memory footprint for the kernel (the kernel package is just 27.8 Mb, and only a tiny fraction of the files in that package are ever loaded into memory).

Karmic runs very well on my old athlon 1.86 GHz, so it should run fine on a p4 1.8 GHz.

---

### Post by jacobs444 on 2009-11-25
OK its more than just the kernel, but the rule still applies, linux, like any other OS gets slower on every release.

---

### Post by liquider on 2009-11-25
> **Lu Seraph said:**
> but my processor is stressed to the max
What do you mean? If you have a process eating up your whole CPU, you can find and kill it with
```

$ top

```

---

### Post by jocko on 2009-11-25
> **jacobs444 said:**
> OK its more than just the kernel, but the rule still applies, linux, like any other OS gets slower on every release.
Not true. I haven't done any benchmarks to confirm it, but my computer works at least as well now with karmic as it did with warty warthog four years ago. I actually think a benchmark would say the overall performance is better now, as the kernel is better and faster, most of the hardware drivers perform better, the ext4 filesystem is faster than old ext3. The total memory usage may be a bit higher now than four years ago, but that would not cause the symtoms the op describes (as he says he still has free memory).

---

### Post by jacobs444 on 2009-11-25
what i said is very true, just look at the phoronix benchmarks.

---

### Post by jacobs444 on 2009-11-25
anyway, i'll not reply again, someone should be helping this guy instead of us arg
uing.

---

### Post by jocko on 2009-11-25
> **jacobs444 said:**
> anyway, i'll not reply again, someone should be helping this guy instead of us arg
uing.
I can agree with that.

@OP:
Does your computer run better from a live cd than your actual install?

Is there any particular process that uses a lot of cpu?
- Type "top" in a terminal and look at the output. Is there one particular process that stays on the top of the list most of the time? How high cpu usage does that process have?

How much memory is really used?
- Type "free -m" in a terminal and post the output here.

---

### Post by Luka Batistic on 2009-11-25
> **Lu Seraph said:**
> I'm only using about 317MB of ram on average, **but my processor is stressed to the max.**

There's your answer (maybe :)).

Start up System monitor and see which process is eating up your CPU. Should be easy to fix once you find out what's slowing your computer down.

Writing this on a 900MHz Celeron with 1gb of RAM and a snappy Ubuntu Karmic :P

---

### Post by khelben1979 on 2009-11-25
I think your graphics drivers might be part of the problem. Check it up and report back in this thread. Open source graphic drivers are usually slow.

Also, take a look at the sound device drivers as well. If it uses your sound chip instead of your sound card (if you have one) you get a big slow down as well.

---

### Post by Lu Seraph on 2009-11-25
OK here's the result of "top" in terminal.

seraph@Lu-Seraph:~$ top

top - 12:46:59 up 12:44,  2 users,  load average: 2.58, 1.84, 1.46
Tasks: 130 total,   1 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s): 82.9%us, 13.2%sy,  0.0%ni,  3.3%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    476980k total,   464184k used,    12796k free,    53812k buffers
Swap:  1397612k total,    54828k used,  1342784k free,   130160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1569 seraph    20   0  477m 178m  26m S 50.7 38.3 476:04.51 firefox            
 1246 root      20   0 70316  18m 6824 S 18.9  3.9 105:02.47 Xorg               
 1773 seraph    20   0 45576  19m  13m S 16.3  4.1 106:59.81 gnome-system-mo    
 2054 seraph    20   0 38216  12m 9672 S  4.6  2.7   0:02.30 gnome-terminal     
 1389 seraph    20   0  156m 2356 1892 S  3.6  0.5  20:55.37 pulseaudio         
 2075 seraph    20   0  2468 1168  884 R  1.0  0.2   0:00.49 top                
 1441 seraph    20   0 96708 6620 5896 S  0.3  1.4   0:04.64 gnome-settings-    
    1 root      20   0  3288 1372 1080 S  0.0  0.3   0:01.79 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.35 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 async/

---

### Post by Lu Seraph on 2009-11-25
seraph@Lu-Seraph:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           465        448         17          0         52        123
-/+ buffers/cache:        272        193
Swap:         1364         53       1311
seraph@Lu-Seraph:~$ 


I never ran it "Live" from the CD. I had windows XP which ran great compared to THIS and then I installed Ubuntu IN windows. 

This week I installed the SAME copy of ubuntu onto my system and overwrote all the other installs that were on here.
I then used my updater to upgrade to karmic. 

I've never had sound or video issues with Ubuntu and this PC before. 
My sound is onboard, I'll figure out how to look at my video specs in a few, unless someone knows the prompt in terminal that I could use off hand to bring up my sound and  video info it would be appreciated!

---

### Post by emachnic on 2009-11-25
May try running the Live CD of Karmic or just doing a fresh install as opposed to installing then upgrading. Sometimes upgrading is a pain and I usually opt for the fresh install with new versions.

---

### Post by wilee-nilee on 2009-11-25
A low ram and a upgrade=problems, but there may be problems with the graphics as well. Download the live cd and see if the speed is still slow, and remember that a cd will run slower anyway.

---

### Post by mr clark25 on 2009-11-25
i dont think ram is the issue, i have a p4 with 256mb of ram and it runs fine. i upgraded from 9.04 using update manager, and it still works fine.

---

### Post by wilee-nilee on 2009-11-25
> **mr clark25 said:**
> i dont think ram is the issue, i have a p4 with 256mb of ram and it runs fine. i upgraded from 9.04 using update manager, and it still works fine.

I have a dell laptop that has a 1gig chip and 512 ram that runs slow compared to my netbooks 1.6 atom and 2 gigs ram. 256 is pretty low even for Ubuntu, I think if you bumped the ram you would notice a marked difference.

---

### Post by khelben1979 on 2009-11-25
Give us your output of the graphics hardware by doing:
```
lspci
```

---

### Post by ikacer on 2009-11-25
> **Lu Seraph said:**
> seraph@Lu-Seraph:~$ top

top - 12:46:59 up 12:44,  2 users,  load average: 2.58, 1.84, 1.46
Tasks: 130 total,   1 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s): 82.9%us, 13.2%sy,  0.0%ni,  3.3%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    476980k total,   464184k used,    12796k free,    53812k buffers
Swap:  1397612k total,    54828k used,  1342784k free,   130160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1569 seraph    20   0  477m 178m  26m S 50.7 38.3 476:04.51 firefox            
 1246 root      20   0 70316  18m 6824 S 18.9  3.9 105:02.47 Xorg               
 1773 seraph    20   0 45576  19m  13m S 16.3  4.1 106:59.81 gnome-system-mo    


well, firefox should NOT be using 50% of you cpu, same with xorg at 19%.

Also, almost all of your RAM is used up, along with a sizable chunk of swap. So I'm wondering what is using all that memory. Could you run top again, and this time sort it by memory usage (use < and > to select which column the results are sorted by), and post the results again.

---

### Post by Lu Seraph on 2009-11-25
See this is why I'm asking because I've run this the same way on computers that were much MUCH older.

How fast you think something is compared to what you're used to is marked. So if you're using a system that has 2G of ram my less than 500 may seem slow to you.

To me this is pretty fast, this system. It's a new machine for me and I've never owned a computer with more than 1G ram and the best processor I've ever had was an AMD athlon 64 2800+ and I bought that over 5 years ago. Actually just about 5 years ago!


It's not that I'm using an clunky old junk bot.

Ubuntu ran awesome on this unit when I first got it along side a windows partition which also ran pretty well.
This is a computer that is capable of running as fast as I need it to run and doing the things I need it to do.

However it's still way too slow and I need to figure out why and Fix It.

I'm not able to use a CD on this computer. I have no disk drive at the moment and I don't feel like rigging up the other computer to it and borrowing the drive. Because haha The CD drive on my white computer does not come out easily and I just hook them up side by side to borrow the cd drive. I don't have a working burner. 

I don't feel like sitting here with a slow computer while I wait for a cd in the mail and then rigging up my two computers together for it to just do this to me again.

Solutions?

If it's a video issue I never had it before. How could I figure that out?


Oh and the sound works now. The cat chewed the speaker cords...that's all I need eh?

---

### Post by emachnic on 2009-11-25
Could create a Live USB...unless the comp is too old to boot from USB

---

### Post by Roasted on 2009-11-25
> **jacobs444 said:**
> OK its more than just the kernel, but the rule still applies, linux, like any other OS gets slower on every release.

Incorrect.

---

### Post by khelben1979 on 2009-11-25
> **Roasted said:**
> Incorrect.

Agreed.

---

### Post by Lu Seraph on 2009-11-25
Live USB won't happen either I have One USB drive that will work that way I tried my camera as a flash drive to boot and no dice.

The only thing I could boot off is my external drive which is FULL *sigh*

I had to  make room on it just to back the 80 gigs of this pc up.

It's not too old to boot from USB it's not ancient LOL It's just not "New" This thing runs anything I need it to with ease when it works right. And I just put the new OS on after a format so I'm not going to do that again to have the same results and take all my time doing that for nothing.

This is a clean install, reinstalling won't change a damned thing if I have new issues with karmic. 
There has to be something that isn't working as it should and it will be the same next time I install. So should I just remove the upgrade somehow and say to hell with karmic?

It worked fine before I installed it but someone on here has to know why it's not working on karmic! There has to be a fix somewhere.

---

### Post by egalvan on 2009-11-25
> **Lu Seraph said:**
> 



 **I click on something **and wait at least a minute before it actually opens and when it does there's 10 of em because..so I **double click** and ten of them pop open a few minutes later. 

three clicks, and you get ten instances.

> 
**I clicked on it maybe twice, then I right clicked and selected "browse folder" finally it opens. OVER 100 TIMES.**

It took me seriously 5 minutes to close them all. 


two clicks and you get over one hundred instances.


maybe your cat chewed on the keyboard or mouse cables?

How to explain the extra requests for program starts?

---

### Post by doas777 on 2009-11-25
> **jacobs444 said:**
> anyway, i'll not reply again, someone should be helping this guy instead of us arg
uing.

perhaps that is the case, but the op's 12 year old hardware is the likely culprit. Diagnosis: upgrade. Prognosis: terminal.

Op, You can do it if you reallllllllly try, but my advice is either upgrade your hardware (even 5 year old kit is fine), or select a minimal distro like DSL.

---

### Post by Lu Seraph on 2009-11-25
I don't need to upgrade anything at all. It should work just fine. 

Upgrade this, I've run faster pentium 2 systems with ubuntu.

My old computer is not the issue. It ran FAST before I reinstalled.

If you'd be so kind as to give me money, I'd be happy to buy a new computer. Some of us feed children and pay bills with our money and thus I use linux because it's free and runs FAST on older computers. If it ain't broke don't replace it.

The keyboard and mouse are even older and work just fine, always have, always will.

And just to top it off my 17" CRT  in brilliant yellow works freaking awesome like my old skool KOSS hard drivers. 

Now the multiple instances of clicking and opening are totally due to the lagg in the system any one can see that .

So the next person to post, please let me know how to diagnose if this is a video issue or not or some other USEFUL information so I can spend less time on here and more time fixing the problem! Thanks!

---

### Post by khelben1979 on 2009-11-25
> **Lu Seraph said:**
> I don't need to upgrade anything at all. It should work just fine.

I agree. Sounds silly to upgrade the hardware just because of Ubuntu. Maybe you should consider using another distribution instead?

[Comparison of Linux Distributions]("http://en.wikipedia.org/wiki/Comparison_of_linux_distributions") (It might not be up to date, but the most important thing is that it mention it's alternatives).

---

### Post by doas777 on 2009-11-25
> **Lu Seraph said:**
> please let me know how to diagnose if this is a video issue

then I suggest you respond to [khelben1979]("http://ubuntuforums.org/member.php?u=443262")'s request for the output of lspci, so we know what kind of card you have.
```
lshw -C Display
``` may also be helpful.

in Intrepid, Januty, and Karmic, a number of older video cards have been dropped from driver support. anything prior to a geforce 7000 series has been dropped by all but the most basic of drivers, for instance. the min specs for ATI cards have also gone up, and since intrepid, there have been disturbing regressions on older intel integrated cards. sis3 and via have always had touchy support.

so, what you got?

btw, in 2004, I purchased 3 PII towers with everything but hdd, for 9.99$ usd, from the used parts store down the street. you should be able to find p4's at comprable prices now.

---

### Post by DeMus on 2009-11-25
> **Lu Seraph said:**
> OK here's the result of "top" in terminal.

seraph@Lu-Seraph:~$ top

top - 12:46:59 up 12:44,  2 users,  load average: 2.58, 1.84, 1.46
Tasks: 130 total,   1 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s): 82.9%us, 13.2%sy,  0.0%ni,  3.3%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    476980k total,   464184k used,    12796k free,    53812k buffers
Swap:  1397612k total,    54828k used,  1342784k free,   130160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1569 seraph    20   0  477m 178m  26m S 50.7 38.3 476:04.51 firefox            
 1246 root      20   0 70316  18m 6824 S 18.9  3.9 105:02.47 Xorg               
 1773 seraph    20   0 45576  19m  13m S 16.3  4.1 106:59.81 gnome-system-mo    
 2054 seraph    20   0 38216  12m 9672 S  4.6  2.7   0:02.30 gnome-terminal     
 1389 seraph    20   0  156m 2356 1892 S  3.6  0.5  20:55.37 pulseaudio         
 2075 seraph    20   0  2468 1168  884 R  1.0  0.2   0:00.49 top                
 1441 seraph    20   0 96708 6620 5896 S  0.3  1.4   0:04.64 gnome-settings-    
    1 root      20   0  3288 1372 1080 S  0.0  0.3   0:01.79 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.35 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 async/

Adding the percentages of CPU power for the top so many processes give a result close to 100%, meaning the CPU is stressed.
Firefox 50.7
Xorg 18.9
What were you doing at the moment? Watching a flash movie or just browsing with 1 or 2 tabs open? For FF 50.7% is very much. Here, with 3 tabs open I use 1-2%.
Xorg also uses 2%.
This makes me think about a wrong videocard driver making the CPU do a lot of work intended for the GPU.
What videocard do you use and which driver is installed?

---

### Post by samigina on 2009-11-25
Many people has already answer:

Theres some strange problem, because some process are eating too much CPU.

I recommend to make a fresh install, the update use to work bad; so if your system was faster before the update, you can go back to your previous Ubuntu version or put Karmic in a clean install.

You said that you have installed Ubuntu inside windows, I guess using wubi; again, you should install it in the common way, booting from the live cd and choosing Install.

To know if theres some problem with your graphics, try:
- The desktop effects are on? Try to disable it
- Boot in recovery mode, which will load the system in vesa mode (with a basic graphic controller).

---

### Post by QIII on 2009-11-25
> **doas777 said:**
> ...in Intrepid, Januty, and Karmic, a number of older video cards have been dropped from driver support

While this seems *effectively *true, it is not quite the real deal.

What happened is that the OEMs have deprecated support for older cards.  They have become "legacy".

Just so we understand.  OEMs provide drivers for their hardware.

---

### Post by emachnic on 2009-11-25
I say quit complaining about how you think that upgrading should just work and if it doesn't then you're going to be upset. Realize that this is Linux and there are bugs to be worked out. Calm down, buy a 1 GB USB drive and do a fresh install. If you still have issues then come back on the forums.

---

### Post by overdrank on 2009-11-25
Hi, and do not mean to butt in. Did anyone catch the statement on [post #16]("http://ubuntuforums.org/showpost.php?p=8385213&postcount=16").
> THIS and then I installed Ubuntu IN windows. 
Assuming using Wubi. Could this be the issue?

---

### Post by emachnic on 2009-11-25
I know I had issues with Wubi in Karmic so maybe it is a Wubi issue. If you aren't using Windows then there's no reason not to just do a fresh install

---

### Post by Mark Phelps on 2009-11-25
> **Lu Seraph said:**
> 456.8MB memory 
Celeron 1.80Running an older (8.10) version on a 1GHz Celeron with 768MB of memory -- and it runs just fine.  So, the Celeron and the memory aren't the problem.
> I'm only using about 317MB of ram on average, but my processor is stressed to the max.  Later posts showed FF at 50% and Xorg nearly 20%.  That's real high!  Don't know what version of FF you're using, but the newer versions (3.5+) are supposed to use less memory and run faster.  If you're using an older version (3.0x or older), that could be part of the problem.
> I never had any of these issues with my wubi install of ubuntu ever.  It ran slick and fast that's why I didn't fix my windows when I got locked out of it. (I didn't have the code  to activate windows)
So, was Ubuntu working fine BEFORE Windows locked you out? If so, has this performance degradation only been the case since then?  Or has Ubuntu also worked fine since the lock out and this performance problem has only been recent?

---

### Post by ElSlunko on 2009-11-25
Do you have onboard video? Could you post lspci output?

---

### Post by Divider on 2009-11-25
The issue here is simple, you need to switch to xfce or another display manager. GDM eats alot of resources. 

So you can either 

A> use a different display manager.

B> do a real installation, not that "sk" WUBI installer.

C> upgrade your hardware.

D> stop complaining about how something that is free, sucks.

---

### Post by emachnic on 2009-11-25
> **Divider said:**
> The issue here is simple, you need to switch to xfce or another display manager. GDM eats alot of resources. 

So you can either 

A> use a different display manager.

B> do a real installation, not that "sk" WUBI installer.

C> upgrade your hardware.

D> stop complaining about how something that is free, sucks.

Amen.

---

### Post by Vince N on 2009-11-25
Just because it ran fine before dosen't mean it will run fine now.  Stuff changes and hardware support is dropped.  If it ran fine one earler versions of Ubuntu then maybe the newest version of Ubuntu isn't compatable with your hardware.  If we were talking 5 years or less I would agree, but 12 years is ancent in computer terms.  Also sarcastic comments "upgrade this!" and demanding people give you the answers you want isn't going to motivate anyone to help you.  I understand you may be frustrated but theres no reason to jump on people here who are trying to help.  If you don't like their answer, ignore it and move on.
 
Seems to me you have 3 options,
 
1. Remain here and be civil and wait for a solution to come up if one is availible.  (Personally putting it to a console mode and seeing if your having the same CPU and Memory issues would be where I would start but I suspect your hardware simply is no longer up to the task)
2. You can upgrade to better, more current hardware.
3. If 1 dosen't materialize or if your not willing to wait, and 2 is not an option then you can downgrade to a version of Ubuntu you know works with the equipment you have availible.
 
Ubuntu is not magic, I would not expect Windows 7 to run great on your hardware either without having to shut off some features if it would run at all.  Expecting ubuntu to do the same from now till the end of time is unrealistic.

---

### Post by ElSlunko on 2009-11-25
I'm sure he gets what you guys are trying to say, no need to keep chiming in on the same note. Again, what is lspci. It sounds like a video card issue & if it is onboard perhaps its eating up your RAM.

---

### Post by anselm on 2009-11-25
> **overdrank said:**
> Hi, and do not mean to butt in. Did anyone catch the statement on [post #16]("http://ubuntuforums.org/showpost.php?p=8385213&postcount=16").

Assuming using Wubi. Could this be the issue?
Sound's like he is using  wubi instead of a actuall ubuntu install.

---

### Post by lisati on 2009-11-25
> **jacobs444 said:**
> OK its more than just the kernel, but the rule still applies, linux, like any other OS gets slower on every release.
While others might have grounds to object to this, I have a vague idea of what you mean. My previous laptop, with 1.4 GHz Celeron M & 222Mb RAM coped well enough with Feisty (7.04) once it was installed (via the alternate CD), but when I moved to Intrepid (8.10) the system seemed to slow down.
> **anselm said:**
> Sound's like he is using  wubi instead of a actuall ubuntu install.
+1: I never noticed the first time I read the post, but went back. It sure looks that way.

Good luck, everyone as you compare ideas for helping the OP.

---

### Post by Lu Seraph on 2009-11-25
seraph@Lu-Seraph:~$ lshw -C Display
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 65x/M650/740 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff(prefetchable) memory:ed000000-ed01ffff ioport:d000(size=128)



There is my video card. Yes it sucks, no I don't need anything better.

When it was lagging because of firefox I was playing Bejewelled Blitz on Facebook. 
1) My hardware is NOT 12 YEARS OLD!!!!!

2) I do NOT have a Wubi Install. IT WORKED WITH WUBI- IT DOES NOT WORK NOW

3)I AM NOT RE INSTALLING I JUST DID!

4) WUBI RAN BETTER 

5) It ran WITHOUT Karmic Better.

END:

I'm SURE this is a Karmic Video Card Issue.


What's the solution?

Spell it out plain and simple: HOW DO I FIX MY VIDEO ISSUE TO MAKE KARMIC WORK WITH  MY PC?


Oh and anyone who wants to get cheeky with me can have something else from me for free.

I'm looking for HELP not attitude. I'm trying to be civil but I don't feel like buying a new computer. I just bought a p3 and a 360 this month. The pc is not my main gaming machine so I don't need a super fast PC.

It would be nice if I could see what I'm typing WHILE I'm typing it. 

That is all.

---

### Post by doas777 on 2009-11-25
this may be of some limited help:
[http://ubuntuforums.org/showthread.php?t=262331](http://ubuntuforums.org/showthread.php?t=262331)

I understand your frustration, but you have to understand, ubuntu is not a distro optimized for older hardware. the p4 celeron is workable (I had one running feisty, until a year or so ago), but the p2 (which is 12 years if its a day; my first gui computer was a p2 purchased in '96), could find a better fit with dsl or puppy, or one of the more "from scratch" distros. shouting to the sky that this is not the case, does not make you right.

s3 cards have always had problematic support in linux. it is do able, but you are almost always settling for less.

---

### Post by Scott753 on 2009-11-25
I completely understand your frustration. So far, a lot of the advice you have been given is completely worthless, because they have misunderstood the problem. 

Having said that, I think that your reactions have been a little too defensive. Relax and remember that everything gets worked out eventually.

It's hard to figure out fixes for older video cards, simply because fewer people use them, fewer people have experience with them, therefore, fewer solutions are available.

My solution: Go back to 9.04. If it worked well, fast, and was stable, there's no reason to upgrade! Every fresh distro is designed to provide new features and improvements that take advantage of advances in hardware. Since you have an older system, just use the older distro. 

Also, I agree that it is definitely a videocard issue. Firefox simply does not use 50% cpu when it is idle. (When it is not actively performing a command, such as loading a webpage, or playing a game). If right now, as you read this message, Firefox is using >10% cpu, then some of that is being diverted to run the graphics.

---

### Post by Lu Seraph on 2009-11-25
Just curious now that I have no way to format or reinstal with no CD drive and no way to boot from USB , is there a way to dial back my system with an older version of ubuntu?

Will I still be able to use newly updated and developed apps?

Thanks for your help. I wonder how any of these people use Ubuntu or anything that requires thought sometimes. I'm sorry for my defensiveness but as someone who is mildly genius, I don't like it when I have to ask people who aren't bright enough to read a simple post for an answer. 

I really wish that people who don't have a way to help fix my issue would just leave it alone.

Now having all this dealt with, what if I just swapped in a new video card because I could get a newer used card for pennies from my buddy. 

What should I be looking for if I do get a new one, because he's going to tell me "I have a drawer full come grab one"

---

### Post by supermelon928 on 2009-11-25
> **jacobs444 said:**
> OK its more than just the kernel, but the rule still applies, linux, like any other OS gets slower on every release.

I gotta say, I have not experienced what you are describing.

---

### Post by jocko on 2009-11-25
> **Scott753 said:**
> My solution: Go back to 9.04. If it worked well, fast, and was stable, there's no reason to upgrade! Every fresh distro is designed to provide new features and improvements that take advantage of advances in hardware. Since you have an older system, just use the older distro. 

Also, I agree that it is definitely a videocard issue. Firefox simply does not use 50% cpu when it is idle. (When it is not actively performing a command, such as loading a webpage, or playing a game). If right now, as you read this message, Firefox is using >10% cpu, then some of that is being diverted to run the graphics.
His system is not so old that it should have a problem with karmic, and if his graphics card was enough in jaunty it should be enough in karmic as well. There is nothing in karmic that makes it require better hardware than jaunty did. It is simply not true that newer distros require newer hardware. The fact that some operations are slower in newer distros than in older ones (according to benchmarks on phoronix) has nothing to do with changes in hardware support, and I don't think those few accidental regressions have a worse impact on older hardware than they do on newer hardware.

@op:
It could be a graphics problem, but I'm not familiar with the linux driver for S3 cards, so I don't think I can help much with troubleshooting that (but you could attach your /var/log/Xorg.0.log to a post and let someone have a look at it. It may contain some clues).
My advice is to get a karmic live usb and test if that is as bad as the current install. If it seems better, reinstall. Sometimes things go wrong with upgrades (old config files that gets left behind could cause problems in the new software), and the simplest solution is to make a clean install of the new version instead of upgrading from an older.

---

### Post by jocko on 2009-11-26
> **Lu Seraph said:**
> Now having all this dealt with, what if I just swapped in a new video card because I could get a newer used card for pennies from my buddy. 

What should I be looking for if I do get a new one, because he's going to tell me "I have a drawer full come grab one"
First of all, look for agp cards (your computer probably have an agp slot as well as a few pci slots. agp is better).
First I would look for a nvidia card (as new as possible), as nvidia's proprietary graphics driver works really well. I just got a geforce 6200 and it works great for being 5 year old technology.
If you can't find any nvidia cards, go for an ati card. The older cards (radeon 7xxx-9xxx, X7xx-x8xx) should work ok with the open source driver, but may require some tweaking as the default settings for the driver is not very good (at least it wasn't for my radeon 9600 that I just replaced). Semi-new cards (radeon X13xx-X19xx) may be a problem as I think not every part of them works that well with the open source driver yet (tv-out support is missing, not sure about anything else).

---

### Post by Lu Seraph on 2009-11-26
> **jocko said:**
> His system is not so old that it should have a problem with karmic, and if his graphics card was enough in jaunty it should be enough in karmic as well. There is nothing in karmic that makes it require better hardware than jaunty did. It is simply not true that newer distros require newer hardware. The fact that some operations are slower in newer distros than in older ones (according to benchmarks on phoronix) has nothing to do with changes in hardware support, and I don't think those few accidental regressions have a worse impact on older hardware than they do on newer hardware.

@op:
It could be a graphics problem, but I'm not familiar with the linux driver for S3 cards, so I don't think I can help much with troubleshooting that (but you could attach your /var/log/Xorg.0.log to a post and let someone have a look at it. It may contain some clues).
My advice is to get a karmic live usb and test if that is as bad as the current install. If it seems better, reinstall. Sometimes things go wrong with upgrades (old config files that gets left behind could cause problems in the new software), and the simplest solution is to make a clean install of the new version instead of upgrading from an older.

seraph@Lu-Seraph:~$ var
No command 'var' found, but there are 17 similar ones
var: command not found
seraph@Lu-Seraph:~$ log
No command 'log' found, did you mean:
 Command 'klog' from package 'openafs-krb5' (universe)
 Command 'klog' from package 'klog' (universe)
 Command 'klog' from package 'openafs-client' (universe)
 Command 'mog' from package 'mazeofgalious' (universe)
 Command 'vlog' from package 'atfs' (universe)
 Command 'logo' from package 'ucblogo' (universe)
 Command 'rlog' from package 'rcs' (universe)
 Command 'plog' from package 'ppp' (main)
 Command 'xlog' from package 'xlog' (universe)
 Command 'iog' from package 'iog' (universe)
 Command 'eog' from package 'eog' (main)
 Command 'flog' from package 'flog' (universe)
log: command not found
seraph@Lu-Seraph:~$ Xorg.0.log
Xorg.0.log: command not found
seraph@Lu-Seraph:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied
seraph@Lu-Seraph:~$ 

Emm I don't think that worked. Sorry could you give me a little more info on what I should be doing here?

It's just that I can't really do another fresh install because of hardware issues (no disk drive and not enough space on my usb) 

Thanks for your input!

---

### Post by jocko on 2009-11-26
> **Lu Seraph said:**
> seraph@Lu-Seraph:~$ var
No command 'var' found, but there are 17 similar ones
var: command not found
seraph@Lu-Seraph:~$ log
No command 'log' found, did you mean:
 Command 'klog' from package 'openafs-krb5' (universe)
 Command 'klog' from package 'klog' (universe)
 Command 'klog' from package 'openafs-client' (universe)
 Command 'mog' from package 'mazeofgalious' (universe)
 Command 'vlog' from package 'atfs' (universe)
 Command 'logo' from package 'ucblogo' (universe)
 Command 'rlog' from package 'rcs' (universe)
 Command 'plog' from package 'ppp' (main)
 Command 'xlog' from package 'xlog' (universe)
 Command 'iog' from package 'iog' (universe)
 Command 'eog' from package 'eog' (main)
 Command 'flog' from package 'flog' (universe)
log: command not found
seraph@Lu-Seraph:~$ Xorg.0.log
Xorg.0.log: command not found
seraph@Lu-Seraph:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied
seraph@Lu-Seraph:~$ 

Emm I don't think that worked. Sorry could you give me a little more info on what I should be doing here?

It's just that I can't really do another fresh install because of hardware issues (no disk drive and not enough space on my usb) 

Thanks for your input!
The file Xorg.0.log is in /var/log/.
You could copy the file to your desktop with this command:
```
cp /var/log/Xorg.0.log ~/Desktop/Xorg.0.log.txt
```
It contains a lot of text, so don't just paste its content in a post. Make it an attachment to a post.

---

### Post by Lu Seraph on 2009-11-26
Ok , done and done. Thanks again!

See attachment :)

---

### Post by Scott753 on 2009-11-26
to jocko

I am not saying that newer distros require newer hardware (causation), only that the two go hand in hand (correlation). After all, no one wants to have a top of the line computer and then run MS-DOS on it, right? As hardware improves and becomes better, faster, cheaper, OS adapt to take advantage of those improvements.

If he has a problem with karmic, it HAS to be because of a change/lack of hardware support, since the same problem did not occur with 9.04. 


Lu Seraph, And the Ubuntu installation is not that large, couldn't you get another flash drive to put it on? Unless the problem is your bios won't support booting from it... In which case you really need a cd drive, or you could remove the whole hard drive and put it into another computer.

---

### Post by jocko on 2009-11-26
> **Scott753 said:**
> to jocko

I am not saying that newer distros require newer hardware (causation), only that the two go hand in hand (correlation). After all, no one wants to have a top of the line computer and then run MS-DOS on it, right? **As hardware improves and becomes better, faster, cheaper, OS adapt to take advantage of those improvements.**

If new hardware is better, faster and cheaper, and the developers want to take advantage of that why would that automatically make the os run poorly on older hardware? That's just not logical. If it was true it would just be a sign of lazyness (I suspect that this is what microsoft said before they released vista: "hey, most new computers have more than 1 Gb ram anyway, so it doesn't matter that the new os will need 760 Mb just to boot... so we don't need to make it work better").

In the long run of course newer distros will require more than older distros, but just not on the time scales were dealing with here. What has happened in the six months between jaunty and karmic that would force the developers to make a computer that worked perfectly fine in jaunty behave like if it was an antique in karmic?
There has been no really great change in any of the software (just newer versions of most things, but nothing that would cause any difference in hardware requirements or performance).


Karmic runs as smoothly on my computer (similar in age and cpu performance as Lu Seraph's, but with more RAM and a better graphics card) as jaunty and all previous ubuntu versions I have used did.
If he notices such a huge degradation in performance as he describes, either there is something seriously wrong with his install or there is a serious bug affecting some of his hardware.
If someone on the other hand would have a >10 years old computer and would notice similar problems in karmic compared to breezy badger I would not be surprised...

---

### Post by Scott753 on 2009-11-26
ok

---

### Post by _aXXe_ on 2009-11-26
Since my upgrade (fresh Install) from 8.04 to 9.10 I have experienced VERY slow response also. I have An Intel P4 Dual core with 3 Gig of RAM, A Nvidia 7300 LE video card and a small SATA 100 Gig HD.

ME, 2000, XP ran fine. Windows 7 was junk. I don't dual boot.

Below is information requested is several of the previous replys.





top - 11:09:48 up 23:59,  2 users,  load average: 0.02, 0.04, 0.01
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.1%us,  0.3%sy,  0.0%ni, 97.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3096536k total,  1015796k used,  2080740k free,   107536k buffers
Swap:  4811428k total,        0k used,  4811428k free,   543404k cached




christopher@christopher-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
04:04.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
04:05.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
christopher@christopher-desktop:~$ 


I really enjoy LINUX and I'm curious as to why this is happening.

I'm a newbie of sorts and I need to understand so I can make a decision as to whether I need to continue with 9.10 or return to 8.04


Thanks,

Chris

---

### Post by cascade9 on 2009-11-26
> **doas777 said:**
> the p4 celeron is workable (I had one running feisty, until a year or so ago), but the p2 (which is 12 years if its a day; my first gui computer was a p2 purchased in '96), could find a better fit with dsl or puppy, or one of the more "from scratch" distros. shouting to the sky that this is not the case, does not make you right.
 
 s3 cards have always had problematic support in linux. it is do able, but you are almost always settling for less.
 
 P2s came out in may, 1997. Your 96 computer would have been a pentium 1. 
 
 Also, the OPs card isnt an S3, its SiS. 

> **Lu Seraph said:**
> Now having all this dealt with, what if I just swapped in a new video card because I could get a newer used card for pennies from my buddy. 

What should I be looking for if I do get a new one, because he's going to tell me "I have a drawer full come grab one"

That may well help. Check to see if you have an AGP slot (heres a pic in case you don't know them offhand)-

[http://pc.watch.impress.co.jp/docs/article/20000628/agp.jpg](http://pc.watch.impress.co.jp/docs/article/20000628/agp.jpg)

If you have AGP, get the latest nVidia AGP card you can find in your friends drawer. 

GeForce- old. 
GeForce2- not as old. 
GeForce3- getting decent. Ish. 
Geforce4- not bad (avoid the GF2MX series, they are just 'super' GF2s) 
GeFroce5 (FX)- the minimum I would be looking for. Not that the earlier cards are bad, they would still beat the SiS you have. 
GeForce6- Good! 
GeForce7- the last series of cards nVidia made with an AGP attachment. 

I would be looking for a FX-5600 or 5700, 6600 or 7600. 

BTW, with nVidia, the higher the number in a series the faster the card. So a FX 5600 is not as fast as a FX 5700. Also, when you change series, performance tends to stay similar when you drop models. So a 6800 is about as fast as a 7600. 

> **Scott753 said:**
> If he has a problem with karmic, it HAS to be because of a change/lack of hardware support, since the same problem did not occur with 9.04. 

+1 , Agreed.

---

### Post by cariboo on 2009-11-26
I would suggest it is a graphics adapter problem, most SIS chipsets are not very well supported. I have a system here with an AMD 750Mhz Duron and 512Mb ram, with the smae video chipset as the op. Using the onboard graphics adapter Karmic does indeed run slow. I have an Nvidia MX400 that I installed, and performance was then what it should be. The MX4000 has 64Mb ram, so you can't use any affects, but it runs well enough for web browsing.

---

### Post by running_rabbit07 on 2009-11-26
> **cariboo907 said:**
> I would suggest it is a graphics adapter problem, most SIS chipsets are not very well supported. I have a system here with an AMD 750Mhz Duron and 512Mb ram, with the smae video chipset as the op. Using the onboard graphics adapter Karmic does indeed run slow. I have an Nvidia MX400 that I installed, and performance was then what it should be. The MX4000 has 64Mb ram, so you can't use any affects, but it runs well enough for web browsing.

[Worst Buy]("http://www.bestbuy.com/site/Video-Graphics-Cards/PCI-Video-Graphics-Cards/pcmcat182300050009.c?id=pcmcat182300050009") has a nice little nvidia card for 35 bucks. I know that money is still money, but we have to do what we have to do. I just had to trash an Intel card for the next higher nvidia card that they have so my daughter can play games on her older machine and now it runs great.

---

### Post by Luka Batistic on 2009-11-27
Or buy a cheap 1gb (or 2gb) usb stick to test out a fresh live version of Karmic and see if you get the same issues. You'll either get the same (or bigger) slowdowns which means for some reason Karmic does not like your hardware or things are going to work as they did under the wubi install.

> **Lu Seraph said:**
> I had windows XP which ran great compared to THIS and then I installed Ubuntu IN windows. 

This week I installed the SAME copy of ubuntu onto my system and overwrote all the other installs that were on here.
I then used my updater to upgrade to karmic.

So you did an upgrade from a previous version (9.04?) to Karmic...
Still new to this ubuntu/linux thing but just from the posts I've read here this might have caused slowdown. Did the newly installed system run fine before you upgraded it to Karmic?

And the USB stick will come handy for future upgrades, troubleshooting and/or repairing stuff so it won't be money out the window even if you do decide to buy new hardware to run Karmic (shouldn't be necessary, I'm running a system simlar to yours and it's working fine - on the level of XP, perhaps slightly slower cause I enabled lots of eye candy).

---

### Post by running_rabbit07 on 2009-11-27
> **Luka Batistic said:**
> Or buy a cheap 1gb (or 2gb) usb stick to test out a fresh live version of Karmic and see if you get the same issues.

With the age of his system, I doubt it will boot from USB devices.

---

### Post by Luka Batistic on 2009-11-27
He can boot from USB - said so in previous posts.

And if I may... One of the bigger reasons this post has 7 pages already is in people not reading what the OP has written about his system (admittedly not all in the original post :)).

1. He was running Ubuntu (we don't know which version) via wubi and it was working fine = his computer is good enough to run Ubuntu (at least previous versions, willing to bet Karmic as well)
2. He installed a fresh install of the version of Ubuntu he was running through wubi and upgraded that to Karmic... Somewhere around here his computer became slow.
3. He can boot from USB but doesn't have/can't use his existing USB stick/external drive (can't remember why anymore)
4. He can not boot from CD

That's why I suggested the above - it's the minimal cost to check whether Karmic is causing the slowdown or something went wrong with the install/upgrade combo. He can check other (older) versions as well to see how they work.
If Karmic is the cause of the slowdown I would still first suggest finding out what exactly is causing this (if possible) before buying stuff which would be beneficial but he might not need or might even not be causing the problem.

Oh, and you can also borrow a friends USB stick to bring the cost to zero :)

---

### Post by running_rabbit07 on 2009-11-27
He also said he isn't willing to reinstall.

---

### Post by some-what-Gnu-2-networks on 2009-11-30
> **Lu Seraph said:**
> seraph@Lu-Seraph:~$ lshw -C Display


There is my video card. Yes it sucks, no I don't need anything better.

When it was lagging because of firefox I was playing Bejewelled Blitz on Facebook. 
1) My hardware is NOT 12 YEARS OLD!!!!!
2) I do NOT have a Wubi Install. IT WORKED WITH WUBI- IT DOES NOT WORK NOW
3)I AM NOT RE INSTALLING I JUST DID!
4) WUBI RAN BETTER 
5) It ran WITHOUT Karmic Better.
END:
Oh and anyone who wants to get cheeky with me can have something else from me for free.
I'm looking for HELP not attitude. I'm trying to be civil but I don't feel like buying a new computer. I just bought a p3 and a 360 this month. The pc is not my main gaming machine so I don't need a super fast PC.
It would be nice if I could see what I'm typing WHILE I'm typing it. 
That is all.


Install Ubuntu on the PS3, assuming it's not a "slim"

---

### Post by waltrothfuss on 2010-01-26
I have a similar problem with 9.10 on a SuperMicro dual-quad opteron motherboard with 8 GB of ram that is only two years old and has an onboard vga.  With 8.10 LTS everything was terrific, very fast.  With a fresh install of UbuntuStudio 9.10, some things are okay but trying to load Filemaker using Codeweaver's Crossover Linux takes more than five minutes, where FileMaker used to load as fast as it did natively on a Windows machine using 8.10.  The same is true of VirtualBox virtual machines, with everything freshly installed on this 9.10 package.  They used to load and run very fast on 8.10, now things are glacial.  I think something is dreadfully wrong with 9.10.  And no, it is not an UbuntuStudio problem, because I tried a fresh install of regular 9.10 and suffered the same problems.  Each time I did a fresh install the hard disk was wiped clean with WipeDrive, so there was no upgrade issue onto a pre-existing system.  This is SOOOOO uselessly slow that I am ready to give up and go back to 8.10.  9.10 is just a pretty face.

---

