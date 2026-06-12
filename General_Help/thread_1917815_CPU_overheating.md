---
title: "CPU overheating"
date: 2012-01-30
forum: General Help
---

### Post by ahmedo047 on 2012-01-30
I am using ubuntu 11.1. The ubuntu normally runs when I dont run the program. i.e there is not heating problem. But the CPU is excessive heating (82 degree) when I run the program. 
Intel &#304;7 920 cpu
Asus p6t se motherboard

What should I do?

Thanks in advance

---

### Post by JC Cheloven on 2012-01-30
> **ahmedo047 said:**
> I am using ubuntu 11.1. The ubuntu normally runs when I dont run the program. i.e there is not heating problem. But the CPU is excessive heating (82 degree) when I run the program.
To know which particular program, could give someone over here a clue... 
Giving relevant info will give in turn better answers ;)

---

### Post by ahmedo047 on 2012-01-30
Program: Gromacs software 4.5.4

---

### Post by Bobhuber on 2012-01-30
If your overheating even with the cores running at 100% you don't have sufficient cooling.
It has nothing to do with Ubuntu.
I overclock an MSI board and even running 100% on all 4/cores I don't exceed 55C.

---

### Post by whatthefunk on 2012-01-30
What kind of CPU cooler are you using?  I hope you arent using the one that came with the CPU...  You can get aftermarket CPU coolers for pretty cheap.  Ive never seen my temp go above 50 degrees.

---

### Post by Slim Odds on 2012-01-30
Sound like your CPU is not properly cooled. Did you install it yourself? Did you do it right?

I'm encoding a video right now with all 4 cores maxed out and I'm running at 51C

---

### Post by conradin on 2012-01-31
Your factory i7 heatsink just barely meets the minimum cooling requirements. (read cpu specs) The i7 cores are really intended to operate with liquid cooling and or decent case fans going. scaling may play in to the heating effect, you can perhaps force the cpu into running slower, and thereby cooler. 
This link has helped me in the past.
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by ahmedo047 on 2012-01-31
Thanks for all replies but I have still the same problem.
I am using the all cores at 100%. Now I have 2 PC.
1.first: It has Intel i7 920 CPU and Asus P6T SE motherboard
2.second: It has Intel I7 960 and G&#305;dabyte x58A-UD5 LGA 1366 motherboard. I buy this PC before a week. I have overheating problem since I buy it. Note: it is overheating when I run gromacs. I dont have any heating when I dont run gromacs.
I have been using the 1.first PC for 2 years. I dont have any problem related with this PC before. I am using the gromacs on this PC for 2 years. I dont have any problem so far.
I changed the processors with each other yesterday. i.e. I installed to first PC the i7960 cpu. Then I tested it. I have overheating again.  I installed to second PC the i7920 cpu. unfortunately I have overheating again.
Then, I changed the processors with each other again. i.e They returned the first states. This once, I have the problem of warming/overheating on both computers :(

---

### Post by ahmedo047 on 2012-01-31
> **ahmedo047 said:**
> Thanks for all replies but I have still the same problem.
I am using the all cores at 100%. Now I have 2 PC.
1.first: It has Intel i7 920 CPU and Asus P6T SE motherboard
2.second: It has Intel I7 960 and G&#305;dabyte x58A-UD5 LGA 1366 motherboard. I buy this PC before a week. I have overheating problem since I buy it. Note: it is overheating when I run gromacs. I dont have any heating when I dont run gromacs.
I have been using the 1.first PC for 2 years. I dont have any problem related with this PC before. I am using the gromacs on this PC for 2 years. I dont have any problem so far.
I changed the processors with each other yesterday. i.e. I installed to first PC the i7960 cpu. Then I tested it. I have overheating again.  I installed to second PC the i7920 cpu. unfortunately I have overheating again.
Then, I changed the processors with each other again. i.e They returned the first states. This once, I have the problem of warming/overheating on both computers :(
any suggestions?

---

### Post by Slim Odds on 2012-01-31
> **ahmedo047 said:**
> any suggestions?

Better cooling. A bigger heat-sink. etc. etc.

Is the pad installed properly? There is a heat conducting pad needed between the CPU and the heat-sink. Is it there and properly installed?

Pictures might help.

---

### Post by CatKiller on 2012-01-31
If you've moved the processors around, you'll need to replace the thermal compound. Scrape off the old stuff and apply fresh.

You also haven't said what other cooling you're using, how cramped the cases are or how clogged with dust.

---

### Post by Gremlinzzz on 2012-01-31
> **ahmedo047 said:**
> I am using ubuntu 11.1. The ubuntu normally runs when I dont run the program. i.e there is not heating problem. But the CPU is excessive heating (82 degree) when I run the program. 
Intel &#304;7 920 cpu
Asus p6t se motherboard

What should I do?

Thanks in advance

There was a heating problem with 11.10,
I switched to linuxmint 12 and problem was solved,:popcorn:
[http://askubuntu.com/questions/68730/how-do-i-solve-this-super-11-10-heating-problem](http://askubuntu.com/questions/68730/how-do-i-solve-this-super-11-10-heating-problem)


did you install the updates maybe its been fixed

---

### Post by Slim Odds on 2012-01-31
> **Gremlinzzz said:**
> There was a heating problem with 11.10,
I switched to linuxmint 12 and problem was solved,:popcorn:
[http://askubuntu.com/questions/68730/how-do-i-solve-this-super-11-10-heating-problem](http://askubuntu.com/questions/68730/how-do-i-solve-this-super-11-10-heating-problem)


did you install the updates maybe its been fixed

I read some of that, but there's a ton of stuff there.

Is this related to the Intel chipsets?

I don't have this problem on my laptop with Intel (SU7100)or my desktop with AMD.

---

### Post by ahmedo047 on 2012-01-31
> I am using the all cores at 100%. Now I have 2 PC.
1.first: It has Intel i7 920 CPU and Asus P6T SE motherboard
2.second: It has Intel I7 960 and G&#305;dabyte x58A-UD5 LGA 1366 motherboard. I buy this PC before a week. I have overheating problem since I buy it. Note: it is overheating when I run gromacs. I dont have any heating when I dont run gromacs.
I have been using the 1.first PC for 2 years. I dont have any problem related with this PC before. I am using the gromacs on this PC for 2 years. I dont have any problem so far.
I changed the processors with each other yesterday. i.e. I installed to first PC the i7960 cpu. Then I tested it. I have overheating again. I installed to second PC the i7920 cpu. unfortunately I have overheating again.
Then, I changed the processors with each other again. i.e They returned the first states. This once, I have the problem of warming/overheating on both computers 
 
I tried all methods but I couldnt solve the problem. I tried the following methods but the problem is continuing :(
1) 
gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\" pcie_aspm=force acpi=noirq i915.i915_enable_rc6=1"
 
then, sudo update-grub
2.)I did ubuntu updating
3.)The computer hardware was revised again
...
The most important problem is the following:
I dont have any problem related with old PC before. I was using the Gromacs software on old PC for 1-2 years. Unfortunately now it is excessive heating too :(

---

### Post by ahmedo047 on 2012-01-31
By the way, there isnt any heating problem when the gromacs doesnt run. The CPU is overheating when gromacs run

---

### Post by Slim Odds on 2012-01-31
> **ahmedo047 said:**
> By the way, there isnt any heating problem when the gromacs doesnt run. The CPU is overheating when gromacs run

Is that the only application that you run that stresses your CPU?

Try installing "cpuburn" and see what happens. But be careful.

---

### Post by Cheesemill on 2012-01-31
> **CatKiller said:**
> If you've moved the processors around, you'll need to replace the thermal compound. Scrape off the old stuff and apply fresh.

+1

It sounds like the thermal paste hasn't been properly applied.

I usually find it easiest to put a small blob (about pea sized) on the CPU and then either spread it on thinly with a credit card or just let the pressure of the heatsink spread it out.

---

### Post by JC Cheloven on 2012-02-01
> **ahmedo047 said:**
> By the way, there isnt any heating problem when the gromacs doesnt run. The CPU is overheating when gromacs run
Thanks for answering. It is likely something related to the program. I see in the gromacs site, download section (interesting software BTW)
> WARNING: do not use the gcc 4.1.x set of compilers. They are broken. These compilers come with recent Linux distrubutions like Fedora 5/6 etc. 
So... we're now by gcc 4.6.X ... fedora 5/6 isn't recent at all... it suggest me some isuue with the compilation of the code. Could you by any means use an older compiler to get the binary? Perhaps it's only a matter of that.

---

### Post by ahmedo047 on 2012-02-03
> 
Thanks for answering. It is likely something related to the  program. I see in the gromacs site, download section (interesting  software BTW)
 	Quote:
 	 	 		 			 				WARNING: do not use the gcc 4.1.x set of compilers. They are broken.  These compilers come with recent Linux distrubutions like Fedora 5/6  etc. 			 		 	 	 
So... we're now by gcc 4.6.X ... fedora 5/6 isn't recent at all...  it suggest me some isuue with the compilation of the code. Could you by  any means use an older compiler to get the binary? Perhaps it's only a 
Firstly, thanks for your reply. You asked me "Could you by  any means use an older compiler to get the binary?". No, I am using a new compiler (gcc 4.6). And I am using Gromacs 4.5.4.
What do you suggest? :(

---

### Post by JC Cheloven on 2012-02-03
Looking at the [gcc site]("http://gcc.gnu.org/releases.html"), and assuming as valid the advice at gromacs site, the "newest" recommended gcc compiler would be 4.0.x. That is, something from 2007.

I visited [one of the mirrors]("http://gcc.cybermirror.org/releases/"), where many versions are available. There is for example [gcc 4.0.4]("http://gcc.cybermirror.org/releases/gcc-4.0.4/"). I don't think you'll need all files there (for example I saw at gromacs' that no fortran code is currently in). Hopefully there will be a readme file in the tarball, which can help you to install that version after uninstalling your present one.

Please note that I never installed an old compiler in a recent system myself, and I don't realize what isuues, if any, could arise. But I think you have pretty little to loose, as changes in your system should be easily reversible. EDIT: Nevertheless perhaps you should try in a virtual machine first, just in case...

Cheers !
JC

---

### Post by ahmedo047 on 2012-02-04
I think the problem might caused by X58 chipset.  I need an x58 chipset driver for Ubuntu but I cannot find it on anyl website :(

---

### Post by xyzzyman on 2012-02-04
You may want to try adding this PPA: [https://launchpad.net/~francisbrwn9/+archive/kernels](https://launchpad.net/~francisbrwn9/+archive/kernels)

It has the 3.2 kernel with all the Ubuntu patches (Basically just a recompile of the 12.04 kernel) for 11.10. Alot of people have reported improvements on sandy bridge just from the ASPM and some other fixes that have been backported.

---

### Post by ahmedo047 on 2012-02-04
I still could not figure out the problem :(

---

### Post by ahmedo047 on 2012-02-04
I installed "cpuburn". The CPU temperature is rising just as the Gromacs software.  This might related to the Intel chipsets as "Slim Odds" said before. Where are the X58 Chipset Drivers for Linux/Ubuntu?
[B]atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.22 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:       +3.31 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.00 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.03 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      2163 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed: 2033 RPM  (min =  600 RPM)
POWER FAN Speed:       0 RPM  (min =    0 RPM)
CPU Temperature:     +82.0°C  (high = +60.0°C, crit = +75.0°C)
MB Temperature:      +45.0°C  (high = +45.0°C, crit = +75.0°C)

radeon-pci-0200
Adapter: PCI adapter
temp1:        +60.5°C 

[/B]

---

### Post by pqwoerituytrueiwoq on 2012-02-04
> **Cheesemill said:**
> +1

It sounds like the thermal paste hasn't been properly applied.

I usually find it easiest to put a small blob (about pea sized) on the CPU and then either spread it on thinly with a credit card or just let the pressure of the heatsink spread it out.
actually it varies with the processor and i7s like a vertical line
[http://www.arcticsilver.com/methods.html](http://www.arcticsilver.com/methods.html)

---

### Post by xyzzyman on 2012-02-04
> **pqwoerituytrueiwoq said:**
> actually it varies with the processor and i7s like a vertical line
[http://www.arcticsilver.com/methods.html](http://www.arcticsilver.com/methods.html)

You need to follow pqwoerituytrueiwoq and do the vertical line method and replace that thermal compound (make sure to thoroughly clean the old stuff) before anything else. You're going to overheat and run hot on load no matter what until that's done.

Once it's done and the compound has gone through it's burn-in period, you need to run a cpuburn and stress it like has been suggested to you previously. This isn't a chipset issue and there isn't a driver to install. You are not properly cooling your i7's now that you've swapped them around. Once you've taken the above steps, compare temps while running cpuburn at full throttle and with gromacs and they will most likely be identical.

---

### Post by gbrowning on 2012-02-05
I am running Core 17 920 on x58 chipset. I am over clocked from 2.6Ghz up to 3.2Ghz.
Running all cores at 100% puts the maximum heat stress on yourcomputer. The only time this happens for me is while transcoding files.  The highest temp I have seen is 55C.  This computer is in a room with temperatures that fluctuate around comfortable.
       Heat problems are exacerbated by overclocking, by using higher core voltages to overclock, and by heavy CPU loads.  Of course dust is always a factor. Some CPUs run hotter than others, some chipsets run hotter than others, it takes a lot of tweaking to bring those characteristics into line.  Too much for this blurb.  Having a properly sized power supply can also make a difference but is not usually a heat problem.
      Heat is dissipated using good thermal paste, good CPU fan/cooler and good case fans.  Room temperature can be a factor.
      The cooling fan will have come with a thermal compound attached in the form of a mastic or it will have come with a small amount of thermal paste for you to add during installation.  You will need to replace this material.  Remove the fan, blow all the dust our of the cooling fins, scrape all the old thermal compound off the mating surfaces of the CPU and the heat sink, use new thermal compound on the mating surfaces and put the fan back in place. As you replace the fan ensure that it is plugged into the proper power outlet and that none of the wires interfere with the mechanism of the fan.
      Look at the case fans while they are running and ensure that none of them have been installed backwards.  A good case will typically direct the air in from the lower front and out through the upper back.  There may be a fan that blows directly on the video card, or the memory.  Sometimes these fans fight the direction of flow of air coming off the CPU cooler.  Look at this carefully, you might want to unhook a fan that does this. Gaming cases add fans for marketing purposes and appearance.
    When you next re-boot go into your BIOS and look at the fan settings. There should be controls for CPU fan speed and for the main chassis fan. Typically these will keep the fan running at 100% if the core tempo is above 30C.  Just ensure they are set to run at 100% almost all the time.
    If you are not over-clocked do not play with any of the other settings.
    If you continue to have the high temps after taking these steps you should spend money on a good cooler. This is a good investment for someone who runs near 100% anyway.  It will add lifetime to your system.
    A different route is to Under clock your system but............

---

### Post by Slim Odds on 2012-02-05
Those are all good explanations, but the most likely problem is the CPU to heat-sink issue. Although the CPU fan is next.

Make sure that the thermal transfer from the CPU to the heat-sink is good (pad or paste) and also check that the CPU fan is on and blowing toward the heat-sink.

It's not a software problem.

P.S. Ubuntu release numbers are date based, i.e., year/month. So it's 11.10 (2011/October).

---

### Post by ahmedo047 on 2012-02-07
Thanks to everyone who helped.
I put a new cooler (Thermaltake Friock) on the CPU. The problem is solved.

---

