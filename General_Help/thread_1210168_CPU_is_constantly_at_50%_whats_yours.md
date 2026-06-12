---
title: "CPU is constantly at 50% whats yours?"
date: 2009-07-11
forum: General Help
---

### Post by bodyharvester on 2009-07-11
a question for all,

my dell mini 9 has a 1.6ghz and 2 gb of RAM, standing still it uses as little as 150 mb of RAM but the CPU frequency monitors (there are two) have never been below 800Mhz regularly topping 1.6Ghz

id like to know what your cpu is and what linux you use. i use jaunty 9.04 desktop ed. on a netbook but will put the netbook remix on it in the next few days.

this laptop burns my thighs somethimes:lolflag:
(also what are the Ondemand, Conservative, Performance and Powersaver options? on *EDIT: when i switched to* Powersaver my CPU's stay at 800 MHz)

thanks):P

---

### Post by graham70 on 2009-07-11
Gday 
I am only new but I think you are looking at the "CPU frequency scaling Monitor" or what speed step your cpu is at. My 2ghz laptop normally sits around 1Ghz and sometimes steps up to 2Ghz. But my usages percentage is normally around 15% 
 
I maybe wrong

---

### Post by binbash on 2009-07-11
If it is higher then %2-3, that distro is not stable and there is a serious bug.

---

### Post by bodyharvester on 2009-07-11
yeah, the frequency thing

and,

> **binbash said:**
> If it is higher then %2-3, that distro is not stable and there is a serious bug.

:shock:?

---

### Post by satish_j on 2009-07-11
> **bodyharvester said:**
> a question for all,

my dell mini 9 has a 1.6ghz and 2 gb of RAM, standing still it uses as little as 150 mb of RAM but the CPU frequency monitors (there are two) have never been below 800Mhz regularly topping 1.6Ghz

Are u facing any performance issues because of it?
Iam using Hardy and my CPU consumption is around 25% at idle time.Working with applications,this figure goes upto 60%.My memory consumption is also 50% under idle condition.
I think this is OK unless you face any performance issues..

---

### Post by credobyte on 2009-07-11
> **binbash said:**
> If it is higher then %2-3, that distro is not stable and there is a serious bug.

I hope it was a joke ? :roll: I haven't seen my CPU going lower than 20% ( 30-50% is what I see when only Firefox is turned on ).

---

### Post by bodyharvester on 2009-07-11
there are no problems at all

my thighs may occasionaliy burn though:p

---

### Post by agurk on 2009-07-11
graham70 is right, the CPU Frequency Scaling Monitor applet does not show CPU load, it shows what sleep state your processor is in.

If you're interested in CPU load, run 'top' in a terminal, or check System -> Administration -> System Monitor -> Resources.

---

### Post by prshah on 2009-07-11
> **binbash said:**
> If it is higher then %2-3, that distro is not stable and there is a serious bug.

> **credobyte said:**
> I hope it was a joke ? :roll: I haven't seen my CPU going lower than 20% ( 30-50% is what I see when only Firefox is turned on ).

No joke; on my 800Mhz laptop, during idle, I usually see 3%-5%% intermittent usage. Except when opening or closing files or programs, it rarely goes above 25%-40%.

On my dual-core desktop, during idle, I see 0% cpu usage (guess it's rounding down).

As a check, I ran top before replying to this post, and here's the results (Polled 10 times, 10 secs delay). This is with FireFox and QuodLibet active, compiz etc. As you can see, it doesn't go above 25% (except for that spike at 52% god knows what that is; perhaps a song change?) ```
Sat Jul 11 @15:25:35:~$ top -b -n 1 -d 10 | grep -i "cpu(s)"
Cpu(s): 15.8%us,  3.4%sy,  1.6%ni, 75.6%id,  3.4%wa,  0.2%hi,  0.1%si,  0.0%st
Sat Jul 11 @15:26:09:~$ top -b -n 10 -d 10 | grep -i "cpu(s)"
Cpu(s): 15.8%us,  3.4%sy,  1.6%ni, 75.6%id,  3.4%wa,  0.2%hi,  0.1%si,  0.0%st
Cpu(s): 11.6%us,  3.1%sy,  0.1%ni, 85.0%id,  0.1%wa,  0.1%hi,  0.0%si,  0.0%st
Cpu(s): 12.5%us,  2.4%sy,  1.3%ni, 83.7%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Cpu(s): 12.3%us,  3.1%sy,  0.1%ni, 84.4%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Cpu(s): 25.5%us,  5.5%sy,  1.1%ni, 67.7%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Cpu(s): 18.0%us,  3.4%sy,  0.1%ni, 78.1%id,  0.3%wa,  0.1%hi,  0.0%si,  0.0%st
Cpu(s): 15.3%us,  3.9%sy,  1.1%ni, 79.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu(s): 52.8%us,  4.6%sy,  0.1%ni, 40.9%id,  0.8%wa,  0.3%hi,  0.5%si,  0.0%st
Cpu(s):  9.7%us,  1.5%sy,  1.1%ni, 87.3%id,  0.4%wa,  0.1%hi,  0.0%si,  0.0%st
Cpu(s):  8.3%us,  2.4%sy,  0.1%ni, 88.9%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st

```

---

### Post by credobyte on 2009-07-11
> **prshah said:**
> No joke; on my 800Mhz laptop, during idle, I usually see 3%-5%% intermittent usage. Except when opening or closing files or programs, it rarely goes above 25%-40%.

On my dual-core desktop, during idle, I see 0% cpu usage (guess it's rounding down).

Then what's wrong with System Monitor ? I usually see hight CPU usage, however, I don't feel it ( applications are running just fine ) :roll:

---

### Post by kixome on 2009-07-11
I just had mine at 80% usage, found it was the trackerd search and indexing daemon

---

### Post by DeMus on 2009-07-11
Look at the picture and see that all 4 cores are at 100%. It has been like this for 1 1/2 year already. I run a program called Boinc from the University of Berkeley California. It has multiple projects, one of them is called Seti: Search for Extra Terristrial Intelligence at home. I donate my computer power to this project and try to get as many credits as possible. The program has a very low priority, as soon as I do something with the computer, the Seti program gets less CPU power. So, it doesn't bother me, and when I am away the program can take the full 100%.

---

### Post by 3rdalbum on 2009-07-11
Run the "top" command; even an Intel Atom CPU should not be continually running that hard. Everyone whose computer "idles" at 10% or greater: this is not normal behaviour and it is a symptom of a runaway process eating up processor time.

Laptop and netbook users: Run Intel Powertop (sudo powertop) and follow its suggestions, and also follow the suggestions on [www.linuxpowertop.org](www.linuxpowertop.org).

---

### Post by prshah on 2009-07-11
> **credobyte said:**
> Then what's wrong with System Monitor

That's just it; there _is_ something wrong with System Monitor's CPU usage graph. It's a known bug. See [https://bugs.launchpad.net/bugs/206479](https://bugs.launchpad.net/bugs/206479) and [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847)

---

### Post by jolx on 2009-07-11
I'm pretty sure OP is referring to the lowering of the cpu multiplier to achieve a lower clock speed and save energy.

> **bodyharvester said:**
> also what are the Ondemand, Conservative, Performance and Powersaver options?

performance runs cpu at full speed all the time
powersaver runs cpu at lowest stepping available
ondemand will switch between available steps based on usage (when cpu usage rises, speed will as well)
conservative is similar to ondemand. I don't know much about this one as my e6750 only has two available steps, 2 & 2.67GHz

---

### Post by 6205 on 2009-07-11
My desktop is HP dc7900SFF with C2D E8400@3.0Ghz + 2GB Ram, Intel Q45/Q43 chipset with Intel X4500 grapics. 

CPU usage is about cca 20 %, but also system monitor steals cca 5-10%
Banshee on startup eats 16%

F-Spot on startup cca 50 % + scrolling photo library (cca 700 photos) consumes 50-60 % CPU

VLC playing 720p anime is using 50 % CPU

I think there is nothing what we can do about it. Linux applications are simply very resource hungry, badly written or full of bugs. Don't get fooled with low memory usage, that's irelevant.


PS: Also be sure that you have displayed all processes, not only yours..

---

### Post by credobyte on 2009-07-11
> **prshah said:**
> That's just it; there _is_ something wrong with System Monitor's CPU usage graph. It's a known bug. See [https://bugs.launchpad.net/bugs/206479](https://bugs.launchpad.net/bugs/206479) and [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847)

Thnx, but .. why no one can fix it ( bug report was added 2 years ago :o ) ?

---

### Post by bodyharvester on 2009-07-11
> **6205 said:**
> PS: Also be sure that you have displayed all processes, not only yours..

:P actually i just did see all processes, its only using as little as 20% when all are taken into account but the sys monitor does still report high usage, its not wrong, my crispy thighs know its using a lot of power:lolflag:

if this is a bug how can there be no fix? sounds fishy to me

EDIT: on powersaver my cpu's both stay at 800MHz

i cool it down by turning it upside down and fanning it with a piece of card or somehting:D

---

### Post by bodyharvester on 2009-07-11
HOLY HELL! i ran "top" and saw this


joseph@joseph-laptop:~$ top

top - 14:23:52 up  3:14,  2 users,  load average: 1.25, 1.23, 1.38
Tasks: 132 total,   2 running, 129 sleeping,   0 stopped,   1 zombie
Cpu(s): 63.5%us, 14.0%sy,  0.0%ni, 21.4%id,  0.0%wa,  1.0%hi,  0.2%si,  0.0%st
Mem:   2052648k total,   958344k used,  1094304k free,    59772k buffers
Swap:   377488k total,        0k used,   377488k free,   510092k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2641 root      20   0  359m  49m  14m R   62  2.5  64:20.75 Xorg               
 5696 joseph    20   0 40516  20m  14m S   36  1.0  50:41.36 gnome-system-mo    
15439 joseph    20   0 90440  73m  14m S   19  3.7   0:07.64 gnome-app-insta    
15332 joseph    20   0 33888  14m 9660 S    8  0.7   0:03.67 gnome-terminal     
 3395 joseph    20   0 29952  21m 6824 S    4  1.0   4:18.00 compiz.real        
 4509 joseph    20   0 58320  37m 6852 S    2  1.9   7:41.26 wish8.5            
13328 joseph    20   0  214m  81m  26m S    1  4.1   4:43.00 firefox            
 3396 joseph    20   0 42236  25m  14m S    1  1.3   1:42.53 gnome-panel        
15413 joseph    20   0  2448 1188  912 R    1  0.1   0:00.66 top                
 2402 messageb  20   0  3112 1436  832 S    0  0.1   0:08.86 dbus-daemon        
 2441 haldaemo  20   0  6664 4656 3860 S    0  0.2   0:11.81 hald               
 2672 root      20   0 16520 2828 2288 S    0  0.1   0:05.52 NetworkManager     
 3554 joseph    20   0 16816 5788 4400 S    0  0.3   0:43.20 gnome-screensav    
    1 root      20   0  3084 1888  564 S    0  0.1   0:01.74 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.06 migration/0        

HOW IS ROOT USING 62%? i thought it was a "user" or something?

---

### Post by Hobgoblin on 2009-07-11
> **bodyharvester said:**
> 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2641 root      20   0  359m  49m  14m R   62  2.5  64:20.75 Xorg               

....

HOW IS ROOT USING 62%? i thought it was a "user" or something?

The process is Xorg, the user it is running under is root

---

### Post by bodyharvester on 2009-07-11
> **Hobgoblin said:**
> The process is Xorg, the user it is running under is root

:-s whats "XORG" and why is it running under a user? and also why so much cpu usage?

---

### Post by dhughes on 2009-07-11
> **bodyharvester said:**
> :-s whats "XORG" and why is it running under a user? and also why so much cpu usage?

 It's the window manager app. in other word the Graphical User Interface (windows, menus etc.) you are looking at right now.

---

### Post by bodyharvester on 2009-07-11
> **dhughes said:**
> It's the window manager app. in other word the Graphical User Interface (windows, menus etc.) you are looking at right now.

ahh, thanks, a little knowledge goes a long way :)

---

### Post by Hobgoblin on 2009-07-12
> **bodyharvester said:**
> and why is it running under a user?
All processes have to have an associated user.

> and also why so much cpu usage?

I don't know, what else is going on on your system?

Xorg on my atom powered EeePC uses about 3% when the system is idle but opening a window will make it shoot up briefly, having system monitor running puts it up to around 30%.

---

### Post by Finalfantasykid on 2009-07-12
I find the System monitor will use something like 25% of your cpu when it is enabled(you can reduce this be lowering the number of times it is updated).  Check over in the processes tab and look for gnome-system-monitor chances are it will be decently high cpu.

---

### Post by bodyharvester on 2009-07-14
now im on the Ubuntu Netbook Remix here is another screenshot on my system monitor when firefox and a conversation in amsn were open...cpu usage is soooo low :)

---

### Post by TeamJ on 2009-07-14
I found the same. around 40% constant on my dual-core 2gghz. but switching to UNR fixed it
I think the driver for intel graphics needs too much CPU

---

### Post by bodyharvester on 2009-07-14
> **TeamJ said:**
> I found the same. around 40% constant on my dual-core 2gghz. but switching to UNR fixed it
I think the driver for intel graphics needs too much CPU

possibly, do you think that means ill get better graphics performance?

or dare i say it, be able to run DOOM 3 again?

tried that on my mates vista but even as admin doom 3 wont work:mad:

---

### Post by TeamJ on 2009-07-14
perhaps so. since most netbooks run intel GMA, it was worked around on UNR. I have been using high graphics games without a hitch. but I guess integrated graphics will never be the best option for gamers

---

### Post by bodyharvester on 2009-07-14
cool, ill try DOOM 3 tonight, the disk is at my mates house, and ill post here if the cpu diff has had any effect on performance of graphics with such a game :)

---

### Post by mcduck on 2009-07-14
> **jolx said:**
> I'm pretty sure OP is referring to the lowering of the cpu multiplier to achieve a lower clock speed and save energy.



performance runs cpu at full speed all the time
powersaver runs cpu at lowest stepping available
ondemand will switch between available steps based on usage (when cpu usage rises, speed will as well)
conservative is similar to ondemand. I don't know much about this one as my e6750 only has two available steps, 2 & 2.67GHz

Conservative defaults to lowest available speed, and then gradually switches to higher speeds based on demand.

Ondemand defaults to lowest speed, and immediately jumps to full speed when needed.

On any modern CPU the best option is Ondemand, giving the same performance as running at full speed all the time while also providing the lowest power usage. (The best approach with modern processors and the way they save power is to do CPU-demandig tasks as quick as possible and then switch back to power saving mode).

Performance and Conservative modes can be useful in some special situations, Conservative will just waste more power than Ondemand does

***
And then it's time to mention that's long as you have proper graphics drivers installed etc, so everything is working as it should and your CPU isn't doing the work of graphics card or anything, your processor should spend most of the time in the lowest available speed. And that speed depends on your CPU model and switches in the steps your CPU supports. There really isn't any point in comparing this number between other systems. If you are interested in how's your COY doing then monitor the CPU usage, not frequency. :)

---

### Post by Student Driver on 2009-07-15
I have a Dell Mini 9 as well, and using Conky I see around 10% with Ephiphany and Banshee open and idle, in addition to being connected via Bluetooth PAN to my G1.  When I close everything, it idles to around 1-3% due to Conky and other minor services.  As a side note, it will stay at 50*C or less when things aren't going on.  The better CPU usage and temps are why I am sticking with Ubuntu (Netbook Remix in this case, but using the normal desktop) and not going back to Windows 7.

Now, if using Firefox, it will jump to 25-30% while "idle" (yeah, right) and can shoot up to 64*C with all the crap Firefox thinks it needs to do.  I hope that 3.5 will cure a lot of this excess behavior, but I have Epiphany so I'm good either way.

---

### Post by philcamlin on 2009-07-15
mine is at a constant 2-3 % but then when firefox is on its like maybe 27-28%

---

### Post by lordyosch on 2009-07-15
According to system monitor I am running at...

0% 2% 4% 0% on my quad.


Jay

---

### Post by egalvan on 2009-07-15
33 replies so far and only one had mentioned that the OP is asking about
 CPU SPEED,

> CPU frequency monitors (there are two) have never been below 800Mhz regularly topping 1.6Ghz


and every other reply is referencing 
CPU UTILIZATION


some examples:

[I]0% 2% 4% 0% on my quad.

at a constant 2-3 % but then when firefox is on its like maybe 27-28%
0% 2% 4% 0% on my quad.

at a constant 2-3 % but then when firefox is on its like maybe 27-28%

I see around 10% with Ephiphany and Banshee open and idle

around 40% constant on my dual-core 2gghz. but switching to UNR fixed it
I see around 10% with Ephiphany and Banshee open and idle

around 40% constant on my dual-core 2gghz. but switching to UNR fixed it[/I]

While CPU speed and utilization are related, and can affect each other, they are not the same...

utilization is totally based on how much work the machine is doing,
and speed is based on how fast the cpur runs, and how the frequency can be changed via software/hardware.
Some cpu/bios combos can have very fine-grained speed changes,
some only have "high/lo" or "fast/slow" changes
and some are full-speed-only

---

### Post by HiImTye on 2009-07-15
> **egalvan said:**
> 33 replies so far and only one had mentioned that the OP is asking about
 CPU SPEED,



and every other reply is referencing 
CPU UTILIZATION


some examples:

[I]0% 2% 4% 0% on my quad.

at a constant 2-3 % but then when firefox is on its like maybe 27-28%
0% 2% 4% 0% on my quad.

at a constant 2-3 % but then when firefox is on its like maybe 27-28%

I see around 10% with Ephiphany and Banshee open and idle

around 40% constant on my dual-core 2gghz. but switching to UNR fixed it
I see around 10% with Ephiphany and Banshee open and idle

around 40% constant on my dual-core 2gghz. but switching to UNR fixed it[/I]

While CPU speed and utilization are related, and can affect each other, they are not the same...

utilization is totally based on how much work the machine is doing,
and speed is based on how fast the cpur runs, and how the frequency can be changed via software/hardware.
Some cpu/bios combos can have very fine-grained speed changes,
some only have "high/lo" or "fast/slow" changes
and some are full-speed-only

thank you. I was reading the post thinking the same thing

---

### Post by Yellow Pasque on 2009-07-15
To the OP: your CPU won't go below 800MHz. That's just how Intel SpeedStep works (it lowers the multiplier to 6x and you have a 133MHz Front Side Bus clock, so 6*133 = 800)

---

### Post by rhchia on 2009-07-15
i've nv ran top before. i had system monitor added to the GNOME panel. sometimes the graph's pretty scary like 90% - 100% CPU? when i click on it to show the process, each individual application sum up does not appear to be that high. I only had screenlet running when i play urban terror. When the game suddenly switch from full screen to windowed(i duno why but it happens many times), i happened to see the cpu @ max. :cry:

---

### Post by CompizDoDo on 2009-07-15
Normally my cpu stays above or around 20% 
when i open applications like gtk screen recorder cpu1 gos to like 80% and cpu2 will stay around 20%

---

### Post by bodyharvester on 2009-07-17
doesnt really matter whether its frequency or speed or whatever, its still interesting to compare cpu's in action:)

---

### Post by philinux on 2009-07-17
Athlon 5200+ 2.6 ghz. Always idles at 1gig. Never goes lower than that.

Soon as I run say google earth it goes up to 2.6 briefly. In fact it hit 2.7 lol.

---

### Post by hetx on 2009-07-17
Was surprised to find mine at around 40% until I saw left4dead.exe had been running in the background =D About 5% running movieplayer, banshee, pidgin, firefox

3.6GHz Intel Core Duo

---

### Post by satish_j on 2009-07-18
idle time cpu consumption is around 20%,but the performance seems normal.
Opening firefox causes this figure to increase rapidly...iam thinking to switch to opera..

---

### Post by vinutux on 2009-07-18
mine it use 20 % use with FF and Banshee

---

### Post by taipan_snake on 2009-07-18
I'm using Jaunty on a 731 Mhz Pentium 3..........The CPU is usually idling at about 40%

---

### Post by hawthornso23 on 2009-07-18
> **rhchia said:**
> i've nv ran top before. i had system monitor added to the GNOME panel. sometimes the graph's pretty scary like 90% - 100% CPU? when i click on it to show the process, each individual application sum up does not appear to be that high. I only had screenlet running when i play urban terror. When the game suddenly switch from full screen to windowed(i duno why but it happens many times), i happened to see the cpu @ max. :cry:

Disabling the screen saver fixed the switching out of full screen problem for me. This seems to be a known bug. The best guess seems to be that is that mouse/keyboard activity is not detected properly in some full screen applications and the screensaver tries to start up, thereby ruining your full screen experience. 

I concur with the earlier poster that there is something seriously wrong with system monitor. It seems to be generating most of the reported CPU activity itself. You can see this with an experiment. Go to edit/preferences and change the polling time in the resource tab to once every ten seconds instead of once per second. Watch in amazement as almost all your CPU activity melts away. It seems to be very busy watching itself watch itself watching itself.

---

### Post by Chronon on 2009-07-18
> **bodyharvester said:**
> doesnt really matter whether its frequency or speed or whatever, its still interesting to compare cpu's in action:)

But it's not very useful if everyone is just talking past each other.

My netbook's CPU also idles at 800 MHz and steps up to 1.6 GHz under load.  But I don't find anything terribly interesting about that.

---

### Post by bodyharvester on 2009-07-19
> **Chronon said:**
> But it's not very useful if everyone is just talking past each other.

never said "useful", said interesting, 9.04 has a bug or something, apparently but the netbook remix of 9.04 does not have this problem...

---

### Post by HavocXphere on 2009-07-19
Depends on how you measure it.

e.g. You'll get vast differences between using top and using system monitor's resource page. (The rendering of the graph takes a solid chunk of cpu power).

top-> ~2.5%
sys mon -> ~20%

---

### Post by TeamJ on 2009-07-20
it does not have a bug, only the Intel Driver is crap, this will be fixed in karmic, but in the mean time UNR has a workaround.

---

### Post by HiImTye on 2009-07-28
> **satish_j said:**
> idle time cpu consumption is around 20%,but the performance seems normal.
Opening firefox causes this figure to increase rapidly...iam thinking to switch to opera..

did you install FF 3.5? Shiretoko is fast and takes less resources

sudo apt-get update && sudo apt-get install firefox-3.5

:D

don't forget to go to system > administration > preferred applications and add the '-3.5' to the end of firefox

---

### Post by HiImTye on 2009-07-28
> **HiImTye said:**
> did you install FF 3.5? Shiretoko is fast and takes less resources

sudo apt-get update && sudo apt-get install firefox-3.5

:D

don't forget to go to system > administration > preferred applications and add the '-3.5' to the end of firefox

also, if you use AWN, add (Shiretoko) to the name of your application or it will add a new 'task' rather than grouping it to the firefox one

---

### Post by bodyharvester on 2009-08-06
> **TeamJ said:**
> it does not have a bug, only the Intel Driver is crap, this will be fixed in karmic, but in the mean time UNR has a workaround.

haha, i never even thought about blaming intel, i thought it was just graphics drivers where they dropped the ball :)

---

### Post by burmanabhay88 on 2009-08-06
Change the visual effects to none. That will drop the CPU usage immediately.
> System>Preferences> Appearance. Visual Effects Tab

---

### Post by akrchstn on 2009-08-06
My cpu never really goes past 50% unless firefox is loading a video or has multiple tabs open

---

### Post by SeanBlader on 2009-08-12
If your CPU *NEVER* goes above 50% it's rated clock speed, it means you probably spent 4 times what you should have on your CPU. You could've gotten a system with half the processor speed and spent a quarter of what you did. Although if you have a laptop, notebook or netbook, then you didn't really have a choice. 

If you're looking at your idle time, it means your processor has stepped to it's slower clock speed, which means any little task is going to take twice the processor time because you have half the processor power while it's stepped down. So the slower your processor steps, the harder it has to work to do the little things, like run system monitor, and check network traffic for incoming chatter.

Really the only person in this thread getting her money's worth out of her processor was the one running Seti@home. I tried that on my home system for a little while, but then noticed my electricity bill had doubled, so I stopped. Now I only run it at work.

---

### Post by bcz on 2009-08-16
Am running AMD Phenom II X2 550 cpu

Running 9.04 Gnome distribution with ASUS M4N78-Pro MB, 2 Gb DDR2-800

At idle, with desktop loaded, both CPUs are about 15% average according to system monitor

Am using onboard GPU with dual-monitors 1920x1200 and 1280x1024

Have loaded latest NV drivers and all updates

Processes show 0% utilisation.  I expect XP to be this power hungry and expect Ubuntu to be much more efficient.

Any idea what is going on?  I am planning to use Acer Aspire One with 512Mb, N160 cpu and am a bit concerned.  Do we have a problem here?

Do we need to start a new thread?

Rgds Bill C

---

### Post by lessgov2007 on 2009-08-16
I'm on an old computer, which originally was running Windoze 2000. It only has a 900MHz Athlon with 384MB of Ram and a cheapo Nvidia 6200. My processor usage at idle is around 10-20%, and when doing things it's generally around 80-100%. I'm not complaining though. It runs good enough for me, and I also run compiz. Only thing that really gives my processor a hard time is flash on web pages. I've tried all the tricks, but my old puter just doesn't have the backbone for heavy flash pages, especially stupid MySpace. That's fine with me though. I hate MySpace!

---

### Post by fallenshadow on 2009-08-16
At idle my system is at less than 5% for both cores. I reckon thats what it should be for most people but everyone has different hardware and different versions of Ubuntu.

---

### Post by bodyharvester on 2009-08-18
> **bcz said:**
> At idle, with desktop loaded, both CPUs are about 15% average according to system monitor

Am using onboard GPU with dual-monitors 1920x1200 and 1280x1024

Do we need to start a new thread?

Rgds Bill C

open terminal ant type "top"

ive learned a lot since i started this thread, system monitor uses a load of resources to work, your cpu usage wont be as high as you think

when i wrote the title i meant the cpu frequency scaling monitor things you can put in the toolbars :p

new thread? maybe, i dunno, this keeps appearing from time to time with new replies so i guess people are still looking, but if you need more advise, i think it would be okay to start a new thread for that. i cant see any mods going berserk over someone asking for help ;)

---

### Post by phishStix! on 2009-08-19
What's up, all?

    When my computer sits idle, the CPU averages about 50-65%.  When I run top, or gnome-system-monitor, all the processes only add up to about 5-8%, on average.  I created another user, logged out, logged in as the new user, and the cpu usage (during idle) averages 0-3%.  What can I do to see whatever process/daemon is running away with my CPU?

----------------------

Gateway P-7801u FX Edition Notebook:
     Ubuntu 9.04 w/Gnome 2.26.1 (Kernel 2.6.29-25-server)
     Intel Core 2 Duo (2.21 GHz)

---

