---
title: "Any software available that can reduce computer performance and fan speed?"
date: 2011-10-03
forum: General Help
---

### Post by jammaj on 2011-10-03
Hi All,

I am a fairly new Ubuntu user, having had it for a year now. It is pretty easy to use so I have not become 'advanced' in any way really.

My computer is quite powerful. Despite having a sound reducing shell, the computer still mimics the sound of an aeroplane taking off. All the time. 

I remember back in my Windows days, I had a little performance gadget that allowed me to change the performance capabilities of the computer depending on the task I was doing. I have searched both my brains and the internet, but I cannot for the life of me remember what this was called. I think it came with the Asus motherboard, and had a little picture of a yellow aeroplane on it. It was great for when I was just browsing the internet or watching a film, because when put on the lowered performance options, the sound of the fan would quieten down immensely.

Does anyone know of anything like this available in Ubuntu? I am currently using 34bit 11.04.

Cheers

---

### Post by pqwoerituytrueiwoq on 2011-10-03
try using thinkfan ([FONT=Courier New]sudo apt-get install thinkfan; man thinkfan[/FONT])
you will need to read it's manual
BTW it will not do much for power fans ;) (if they are power fans try something like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16811998808))

---

### Post by gordintoronto on 2011-10-04
What CPU is in your computer? If it's quite powerful, why are you running a 32-bit OS?

In 10.10 I have "gnome applets," which includes cpufreq. My Phenom II X2 has a rated speed of 3.1 GHz, but most of the time it runs at 800 MHz, and the fan just idles. When I run folding@home, the CPU runs at full speed, and the fan cranks up in response to the higher CPU temperature.

---

### Post by jammaj on 2011-10-04
Thank you for the replies.

> **gordintoronto said:**
> What CPU is in your computer? If it's quite powerful, why are you running a 32-bit OS?

In 10.10 I have "gnome applets," which includes cpufreq. My Phenom II X2 has a rated speed of 3.1 GHz, but most of the time it runs at 800 MHz, and the fan just idles. When I run folding@home, the CPU runs at full speed, and the fan cranks up in response to the higher CPU temperature.


Firstly, I am running a 32 bit OS because I found that the 64bit was more unstable, doing things like crashing on shut down.

So the hardware I have is:

AMD PHENOM II X4 965 (3.40GHz/8MB CACHE/AM3) - BLACK EDITION
ASUS® M4A79XTD EVO: DUAL DDR3, S-ATA II, 2 x PCIe x16, 2 x PCIe x1, 2 x PCI
4GB CORSAIR XMS3 DUAL-DDR3 1600MHz (2 x 2GB KIT)
1GB ATI RADEON&#8482; HD 5770 PCI EXPRESS - DirectX® 11
1TB WD CAVIAR GREEN WD10EARS, SATA 3 Gb/s, 64MB CACHE
Sound Blaster® X-Fi&#8482; Xtreme Audio

I have to admit that I am not very knowledgable about computers, apart from that I used to know Windows quite well. My brother built my computer for me. I am striving to be more knowledgeable, and he cannot help me now because he still uses Windows. When I say that using Ubuntu is easy, I mean that the GUI is very user friendly and I have rarely had to extend my knowledge to more complicated matters.

I have just read that my computer is actually cooled by pipes on the motherboard. This led me to download 'xsensors', which provides readings for the computers components. It indicates that I have 3 fans: 2 on the chassis and one on the CPU. Both chassis fans are currently going at around 780rpm. The CPU fan, however, is going at 6400rpm. It indicates that:

CPU temperature = 44C
MB temperature = 38C

Are those readings high? Maybe it is struggling to cool them down for some reason. The only thing I am doing right now on my computer is using Firefox to type this up.

I was just reminded of Cool n' Quiet technology, which I think may have been what I had before, although I distinctly remember disabling this in the Windows BIOS because it kept agitating my system (both computer and humanoid). I am sure that what I had was a yellow airplane thingy, with the options of 'auto' (the computer decides what is best), 'low' and 'high', with the resulting attributes represented on a star plot ([http://mymapclass.blogspot.com/](http://mymapclass.blogspot.com/)).

> **pqwoerituytrueiwoq said:**
> try using thinkfan ([FONT=Courier New]sudo apt-get install thinkfan; man thinkfan[/FONT])
you will need to read it's manual
BTW it will not do much for power fans :wink: (if they are power fans try something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811998808"))

I downloaded this, but it seems a little scary and like it will require a decent amount of time in getting the hang of it. Do you think this would be time well spent, - I.e. that it will sort this out considering what I have just written?

Many thanks

---

### Post by gordintoronto on 2011-10-04
> **jammaj said:**
> ...I have just read that my computer is actually cooled by pipes on the motherboard. This led me to download 'xsensors', which provides readings for the computers components. It indicates that I have 3 fans: 2 on the chassis and one on the CPU. Both chassis fans are currently going at around 780rpm. The CPU fan, however, is going at 6400rpm. It indicates that:

CPU temperature = 44C
MB temperature = 38C

Are those readings high? Maybe it is struggling to cool them down for some reason. The only thing I am doing right now on my computer is using Firefox to type this up.

I was just reminded of Cool n' Quiet technology, which I think may have been what I had before, although I distinctly remember disabling this in the Windows BIOS because it kept agitating my system ...


Your CPU temperature is a little high. Do you know how fast it is running? The fan speed is outrageous.

If it were my machine, I would enable "auto" Cool- n' Quiet. And I would install cpufreqd.

---

### Post by jammaj on 2011-10-05
Thinkfan didn't work. It was giving me an error message along the lines of 'are you sure that this computer is a Thinkpad?' - to which the honest answer was no. It also asked me to use root (sudo), which I did. But it just wouldn't have it.

It seems that this is quite a common problem, as I have found several references to it in the forum and over the internet, with no resolution.

> **gordintoronto said:**
> Your CPU temperature is a little high. Do  you know how fast it is running? The fan speed is outrageous.

If it were my machine, I would enable "auto" Cool- n' Quiet. And I would install cpufreqd.

How do you find out how fast your CPU is running? System Monitor shows that the fiorst core is bumping along at 1-10%, the second core a bit less than this, and the last two cores at only 1-2%.

I do not think it is possible to install Cool n' Quiet on Ubuntu. Most other internet references point to failure in trying to do this. However, I am about to give that a go.

I have also found this link: [http://raftaman.net/?p=450](http://raftaman.net/?p=450) which looks like it could be helpful in fixing the problem.

I will report back.

---

### Post by pqwoerituytrueiwoq on 2011-10-05
add a [FONT=Courier New]CPU Frequency Scaling Monitor[/FONT] to your panel
if you get a error message (or one speed) cool-n-quiet is not enabled (bios setting under advanced -> cpu configuration)
> AMD PHENOM II X4 965 (3.40GHz/8MB CACHE/AM3) - BLACK EDITION
ASUS® M4A79XTD EVO: DUAL DDR3, S-ATA II, 2 x PCIe x16, 2 x PCIe x1, 2 x PCIsame here
my idle temp is 34C atm for my cpu (stock settings/heatsync) fan speed is ~2200 a side air duct make a lot of difference (~10C) 
BTW there is only one  PCIe x16 if you use cross fire (2 GPUs) they become x8

---

### Post by jammaj on 2011-10-05
> **pqwoerituytrueiwoq said:**
> add a [FONT=Courier New]CPU Frequency Scaling Monitor[/FONT] to your panel
if you get a error message (or one speed) cool-n-quiet is not enabled (bios setting under advanced -> cpu configuration)
same here
my idle temp is 34C atm for my cpu (stock settings/heatsync) fan speed is ~2200 a side air duct make a lot of difference (~10C) 
BTW there is only one  PCIe x16 if you use cross fire (2 GPUs) they become x8

How do you add it to the panel in 11.04? I am finding this quite difficult.

I enabled cool n' quiet it in the BIOS. The fan is still whirling around like crazy.

---

### Post by pjd99 on 2011-10-05
I usually use the built in applets, but I remember reading the other day about a piece of laptop/netbook hardware management frontend called jupiter. Looks pretty neat. Seems to work ok.

Project Link: [http://sourceforge.net/projects/jupiter/files/](http://sourceforge.net/projects/jupiter/files/)

There is a .deb on the project site that installs fine on 11.04.

---

### Post by pqwoerituytrueiwoq on 2011-10-05
> **jammaj said:**
> How do you add it to the panel in 11.04? I am finding this quite difficult.

I enabled cool n' quiet it in the BIOS. The fan is still whirling around like crazy.
login to classic mode
clean the dust out of the cpu
install [powernowd](apt:powernowd) that may help i am using it but idk if it does anything for me

---

### Post by gordintoronto on 2011-10-05
In 11.04 Unity, I actually display the CPU speed from within a Conky script. The important part:
${freq_g}GHz

I spelled out the whole thing in issue 51 of Full Circle Magazine, page 40.

---

### Post by Bobhuber on 2011-10-05
1. You need to be running 64 bit (if it's giving you problems there is something else wrong)
2. Enable Amd Cool & Quiet in the Bios (It works fine in Ubuntu and  unless something else is wrong will slow down the fan untill you need it)
3. Idle CPU temp should be around 30C unless you have the thing overclocked which is what it sounds like.

---

### Post by VanR on 2011-10-05
+1 for enabling AMD Cool and Quiet in the BIOS. My computer also has a SMARTFAN function in BIOS also.

---

### Post by jammaj on 2011-10-06
Thanks again to everyone.

Cool n' Quiet seems to be having an effect. The fan speed has reduced to 4800rpm, and I am just about able to hear myself think again.

But it is still loud and annoying. I think that my computer might be overclocked, but I certainly did not do this myself - well, at least not intentionally. 

I will try everyone's suggestions, which will take me some time because I need to learn what, among other things, '.deb' and 'compile' and 'packages' actually means. This is all good for me probably, forcing me out of my languid state and having me engage. Ubuntu is pretty user friendly, so you do not have to learn much at all if you just have basic needs and nothing goes wrong. I shall report back.

But for tonight and this weekend, I shall retreat, and engage once more in non-computer interactions. This all has occupied my last few nights, during which I have crashed Unity a few times via compiz, installed several thousand things that I cannot name nor remember, accidentally made my computer excitedly proclaim that '4 cores are activated!' (I was happy for it), made my eyes bleed and my brain fall out, learned several new things, and perhaps I have grown.

---

### Post by pjd99 on 2011-10-06
FYI, .deb is the type of file the Debian (hence .deb) package management system (dpkg, apt) uses. These are akin to .dmg files for Mac, or .RPM for Fedora/Mandriva. They contain a pre-built version of the software for your operating system and architecture.

If you double click a .deb, Ubuntu Software Centre will open and allow you to install it. (or sudo dpkg -i <package_name.deb> from the terminal)

Compiling means you build the program from its source code. It is much more advanced than using the pre-made packages, and can be a real pain trying to meet all the dependencies for the source you are trying to compile. You might have the program source code, but it may require the source for 4 or 5 other programs before it will attempt to compile. You will need to install build-essential (sudo apt-get build-essential) before trying to compile anything.

Pre-compiled packages may also require others as pre-requisites, but these are usually available and will install automatically with your new program (if not it will fail and tell you the packages you are missing). Especially true if using a frontend like apt-get, Synaptic or Ubuntu Software Centre.

---

### Post by jammaj on 2011-10-10
> **pjd99 said:**
> FYI, .deb is the type of file the Debian (hence .deb) package management system (dpkg, apt) uses. These are akin to .dmg files for Mac, or .RPM for Fedora/Mandriva. They contain a pre-built version of the software for your operating system and architecture.

If you double click a .deb, Ubuntu Software Centre will open and allow you to install it. (or sudo dpkg -i <package_name.deb> from the terminal)

Compiling means you build the program from its source code. It is much more advanced than using the pre-made packages, and can be a real pain trying to meet all the dependencies for the source you are trying to compile. You might have the program source code, but it may require the source for 4 or 5 other programs before it will attempt to compile. You will need to install build-essential (sudo apt-get build-essential) before trying to compile anything.

Pre-compiled packages may also require others as pre-requisites, but these are usually available and will install automatically with your new program (if not it will fail and tell you the packages you are missing). Especially true if using a frontend like apt-get, Synaptic or Ubuntu Software Centre.

Thanks for the help there. The info about .Deb was very enlightening especially, although I am sure I could have Googled it. But cheers nevertheless.


Well, I think all of this computer research might have led me to have a rather debauch weekend, perhaps because the brain needed balancing out. I am still recovering. So I am taking easier this week on both fronts.

Having said that :wink: I have done some more research today and I have found out a few things.

Firstly, the piece of software that worked a treat on Windows was called EPU-4 Engine (later EPU-6 Engine), which came with the ASUS MB. Apparently ASUS just will not put out a version for Linux, and Wine doesn't work well with it. The way it goes, I guess. There appears to be no comparable application for Ubuntu, as evidenced by unsolved threads such as this: [http://ubuntuforums.org/showthread.php?t=1401546.]("http://ubuntuforums.org/showthread.php?t=1401546")

This thread follows the general jist of all other threads and other internet forums that I viewed, I.e. no resolution.

I guess that is really the end of the discussion so far as this forum is concerned, unless someone out there knows a comparable application...

However, for what its worth, I have come up with something of a solution. I went into my BIOS and enabled Cool N' Quiet, which worked quite well (knocked a third of the CPU fan's RPM speed). I then enabled something called 'C1E support', which also helped. lastly, I found a setting called 'Q-fan mode' for both the chassis fans and the CPU fan. I enabled this, and put the CPU fan on 'silent' (other options were 'performance' and 'optimal'). This has reduced the RPM to about 2250, which has made the world of difference.

The resulting CPU temp during idle times is now 47 celcius, which is not too much more than before (44c). It is still quite high, put it appears from my research that the CPU I have lends itself to these temps. Also, MB temp seems to have dropped to 34c (from 38c) for some reason, which is allright by me.

I am about to look into making the chassis fans run at a faster RPM (near the beginning of the thread I mentioned that they were both going only at about 800RPM). I am thinking that pushing up their speed will make up for some of the lost revs of the CPU fan, but shouldn't impact on noise too greatly. Looking inside the computer has been interesting, particularly because I noticed that the chassis fans are much larger than the CPU fan, yet the option of getting them to turn more quickly is not immediately clear (maybe there is no option?). Adjusting their setting sin 'Q-fan mode' to 'performance' didn't make any difference.

I am also thinking of adjusting physical things to make the system cooler - like ventilation and stuff. But this will be for when my wallet is a little fatter I guess (possibly never then).

cheers all

---

### Post by mylocalhost on 2011-10-11
thinkfan is exclusively for IBM/lenovo notebooks

---

