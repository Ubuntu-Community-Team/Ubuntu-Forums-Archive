---
title: "Laptop overheating... where do I start?"
date: 2010-08-29
forum: General Help
---

### Post by karasuman on 2010-08-29
My laptop running Lucid is overheating.  When this happens, it makes an angry, very loud buzzing noise and the screen either goes black or glitches like an NES game, and I have to manually power down.  I have a Dell Inspiron that came with Windows 7; it's only about six months old.  I don't think I had this problem until I updated to Lucid, but that also would have coincided with the ridiculously hot weather we've been having in Pittsburgh, so I'm not sure how to pin down when this started.  This doesn't always happen--length of time the computer is on varies.  Sometimes it doesn't happen at all.  I am pretty sure that it's mostly happened on really hot days.

**What I've Already Tried:**
Someone once mentioned that when he put Ubuntu on his laptop, it overheated because he needed to do something with his bios to make Ubuntu regulate the heat correctly.  I googled for this, and didn't find anything that seemed helpful.
Last time this happened, I waited a few moments and turned it back on, and ran "sensors" from the terminal.  It reported something like 28 degrees Celsius.  I have no concept of how warm that should be, but my husband says that there's no way it was that cool, judging from touch.
I've cleaned the heat vents and elevated the laptop to make sure that the vents on the bottom had access to airflow.

Any help would be appreciated.

---

### Post by mr clark25 on 2010-08-29
just to test if it is the cpu overheating,(sounds like it could be something else) we could put it under load, which makes it produce more heat.

to do this, run these two commands in the terminal:
```

sudo apt-get install pi
pi 100000000

```

trying to calculate pi to the 100millionth digit should keep it under load for a very long time. just close the terminal window to make it stop.

---

### Post by jcolyn on 2010-08-29
To see if your cpu is really overheating install lm-sensors in package manager. Once installed run ```
sudo sensors-detect
``` at the terminal and answer yes to all questions. Once done type```
 sensors
``` at the terminal. This will display cpu temps. If temp is below 60C you're in good shape. 80+C is critical.

You can also check hard drive temp by installing hddtemp in package manager then at the terminal run ```
sudo hddtemp /dev/sda
``` This will show hard drive temp..

---

### Post by Mark Phelps on 2010-08-30
Have seen a LOT more overheating posts with Lucid than with previous Ubuntu versions.  

Hopefully, someone with specific details will tell you how to fix this, otherwise, you will soon burn out the CPU, GPU, and other things -- and end up with an electric brick.

---

### Post by karasuman on 2010-08-30
I haven't really liked any of the flavors since Jaunty, I think.  Any reason why I shouldn't burn an install disc and head on back to that?

---

### Post by bobcollard on 2010-08-30
> **karasuman said:**
> I haven't really liked any of the flavors since Jaunty, I think.  Any reason why I shouldn't burn an install disc and head on back to that?
If you are going to install something and still like something similar to Ubuntu try Linux Mint.  It runs 10 degrees fahrenheit cooler than ubuntu.  I use an application, GKrellM to monitor all my system and hardware.  Find it in Synaptic Package Manager.  It can be set for celsius or fahrenheit   45c is 113f my current temp with several applications running.

---

### Post by karasuman on 2010-08-30
Shouldn't these numbers be the same?

```
beth@grumpy-laptop:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD5000BEVT-75A0RT0: 46°C

```

```
beth@grumpy-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  
temp2:        +0.0°C  (crit = +100.0°C)    
```

Apparently, I don't know what I'm looking at, but my keyboard is very warm.  I'm getting really tired of this and I don't understand what the problem is.  Is it a manufacturing defect in combination with this obscenely warm weather?  Is this a problem with Lucid?

I'm afraid to send my computer back in to Dell because I doubt that they'll be able to reproduce the problem without running the laptop in a stupidly warm environment, which I know they won't do.  I'd also like to HAVE my computer.  I'm about to wipe this partition and go through the hassle of reinstalling Jaunty as soon as the image download finishes.  I know I sound grumpy, and it's because I AM grumpy.  Everything I can do to relax is on this damn machine and I've been working for the past 12 hours.

Any last comments?  Why would the operating system (Lucid) even play a role in this?

---

### Post by libssd on 2010-08-30
> **Mark Phelps said:**
> Have seen a LOT more overheating posts with Lucid than with previous Ubuntu versions.  
Well, not everyone:

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)

AA1 D150 netbook, has been running continuously for the past 2 hours.

---

### Post by Pough913 on 2010-08-30
Buy a fan for it at your local Wal-mart or Best Buy.

---

### Post by rawlins02 on 2010-08-30
@karasuman:  I agree. 

When I first started configuring this Dell Studio XPS 1645 about, oh, 30 days ago (I guess no going back now...) I read about heat issues with this model when running Lucid.  Now, casually browsing the forums:

>sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8 C  (crit = +127.0 C)                  
temp2:       +59.0 C  (crit = +85.0 C)


>sudo hddtemp /dev/sda 
/dev/sda: TOSHIBA MK5056GSYF: 48 C


While it has been warm where I live, I'd also like to determine the source of excess heat.  htop shows no load on CPU at the moment.

---

### Post by Mark Phelps on 2010-08-31
> **libssd said:**
> Well, not everyone:

Where did I say "everyone"??  I said a LOT -- and that is true.

In my case, my PC is NOT running hotter under 10.04.

---

### Post by Mark Phelps on 2010-08-31
> **karasuman said:**
> Shouldn't these numbers be the same?

NO.

The first is the reported temperature of your hard drive.

The second are CPU, and possibly Case, temps.

---

### Post by Mark Phelps on 2010-08-31
> **Pough913 said:**
> Buy a fan for it at your local Wal-mart or Best Buy.

Wal-mart and Best Buy sell laptop fans??

---

### Post by inso_741 on 2010-08-31
this is the reason I use windows 7 most of the time on my laptop
runs cooler and battery lasts longer...windows is simply more efficient than linux...atleast for now

---

### Post by JedMeister on 2010-08-31
FYI there is a kernel bug in Lucid which causes excessive CPU use. This will increase heat and reduce battery life.

From the Lucid Bugs thread:
> **kleeman said:**
> Many laptops are running hot with reduced battery life under Lucid. This bug seems to be the core problem:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281)

A fix that worked for me on two laptops and also for one other user (so far) is to revert to the Karmic kernel:

[http://ubuntuforums.org/showpost.php?p=9388329&postcount=48](http://ubuntuforums.org/showpost.php?p=9388329&postcount=48)

My laptops are running 5C cooler and powertop reveals a more than 50% drop in wakeups.
This is an upstream kernel bug AFAIK (ie not limited to Ubuntu but affects _all_ Linux distros using this kernel version). It still also seems to be affecting the Maverick kernel too. 

If you'd like to be part of the solution have a read over on the bug report (link above) and try some of the patched kernels in [Brian Rodgers' PPA]("https://launchpad.net/~brian-rogers/+archive/power"). 

Otherwise just revert to the latest Karmic kernel (as suggested in the quote). In my experience the Karmic kernel should produce results (ie cooler and longer battery life) similar to WinXP (close but probably not quite as good as Win7).

> **karasuman said:**
> I haven't really liked any of the flavors since Jaunty, I think.  Any reason why I shouldn't burn an install disc and head on back to that?
You could go back to Jaunty but I wouldn't as it is only supported for another 2 months (Oct 2010). If you want to reinstall, Karmic will be supported to Apr 2011. Or just stick with Lucid and use the Karmic kernel.

---

### Post by cloyd on 2010-08-31
The 2.6.32-24 kernel has run cooler for me in Lucid.  As a matter of fact, it runs about like 9.10 did. My only problem, is that this kernel won't print on my Lexmark printer. (other kernels do). 

The fans are a good idea. Also, I bought a quilted looking pad that is filled with some kind of chemical that melts at a low temperature. It seems to cool my machine a degree or two.  Critical temps are different for different processors. Mine says that critical is 100 C. That's hot (boiling point of water). It idles in the 40's, works in the 50's, and goes into the 60 with Flash. I try to keep it out of the 60's by finding another way to view long videos.  I hope this information helps you.

---

### Post by donsy on 2010-08-31
I wonder if the type of processor has something to do with this. I'm  running Lucid on a 5-year-old Celeron with no problems, not even with  full-length video.

---

### Post by riprowan on 2010-08-31
> **karasuman said:**
> My laptop running Lucid is overheating.  

When I installed Lucid on my Lenovo T400 it ran hotter than Hades and battery life was miserable.  The problem was that I have an ATI video adapter and needed to install its driver.  Once I installed the video driver the heat problem vanished and battery life went back to ~3hrs, which is what I got with Win7.

Good luck!  Please let us know what happens.

---

### Post by JedMeister on 2010-08-31
Perhaps the kernel bug I mentioned above is hardware dependent. I have experienced it on a number of machines (desktops as well - but only because I looked for excessive power usage) although retrospect they are all Intel chips manufactured within the last 3 years (3 different Atom chips, a C2D mobile, a C2D desktop and a C2Q desktop).

Sorry if my comments above weren't useful. Hopefully they may be useful to someone though :)

---

### Post by karasuman on 2010-09-01
Is running Lucid with a different kernel as simple as selecting an older kernel from the list when I power up the laptop?

---

### Post by inso_741 on 2010-09-01
> **karasuman said:**
> Is running Lucid with a different kernel as simple as selecting an older kernel from the list when I power up the laptop?
nope but if you want you can compile an old kernel from kernel.org

---

### Post by libssd on 2010-09-01
> **inso_741 said:**
> nope but if you want you can compile an old kernel from kernel.org:confused:

Perhaps you and I define "different kernel" differently. 

Grub (legacy or grub2) offers you a choice of installed kernels during the boot process. Generally, these are minor revisions to the kernel with which a version (e.g., Lucid) was first released, but they are all "different" and if you experience with the latest kernel for that release, you can boot as many generations back as you have installed. Although later kernel releases are supposed to fix problems, it's not unheard of for them to introduce new ones.

---

### Post by inso_741 on 2010-09-01
@libssd : lucid is shipped with kernel 2.6.32 hence grub wont offer previous kernels unless you compile them yourself....maybe you should read the thread [COLOR="Red"]more[/COLOR] carefully before posting

---

### Post by TBABill on 2010-09-01
+26.8C is probably a false reading. My machine (Dell Inspiron 1564) reads the EXACT same anytime, even when it physically feels hot to the touch. So I suspect you have either a similar motherboard not capable of reporting the true readings or the same CPU family (Intel Core i3/5/7)?
 
Here's how I got mine cooler on Ubuntu. First, if you have a proprietary video card driver available - please install and use it. Open source drivers suck for heat on a laptop so far. Protect your machine first, worry about open/closed drivers later.
 
Second, install both Adobe Flash and Sun Java, removing open source flash and java. They don't help a ton, but it does help some.
 
Lastly, use frequency scaling. Install CPUFREQ utilities (via Synaptic), then enable them in a terminal (as ROOT) as follows: > cpufreq-set --governor ondemand
 
Reboot and enjoy.
 
This will force the CPU governor to its lowest capable speed until demand requires increased CPU power. It'll fluctuate to meet demand and return to lowest speed when possible (which is most of the time). 
 
To verify what your cpu governor is set to, use: > cpufreq-info in a terminal. Within the text should be your setting in quotes stated as "ondemand".
 
Those helped cool my machine and they help with any cpufreq capable processor, which is most modern CPUs. Good luck and don't trust that 'sensors' output of 26.8C!
 
Edit: if you upgrade to a newer kernel you will likely have to perform these steps again each time.

---

### Post by libssd on 2010-09-01
> **inso_741 said:**
> @libssd : lucid is shipped with kernel 2.6.32 hence grub wont offer previous kernels unless you compile them yourself....maybe you should read the thread [COLOR="Red"]more[/COLOR] carefully before posting

I understand that, and as I suspected, we're talking about different things when referring to "previous kernels." I was talking about previous kernels for a specific release, while you were talking about kernels from other releases.

The person who asked the question, karasuma, specifically asked "Is running Lucid with a different kernel as simple as *selecting an older kernel from the list when I power up the laptop*?" Perhaps [COLOR="Red"]you[/COLOR] should read the thread more carefully before posting.

---

### Post by karasuman on 2010-09-01
Thanks for all of the advice.  I know just enough about this  get myself in trouble.

I'm so busy with grad school that the idea of making any serious changes to my computer right now makes me want to cry, so reverting to an older version of Ubuntu is at the bottom of my list.  I see the wisdom in choosing the latest long term release, even if the ability to change log-in screens was inexplicably (yes, I know the explanation, but it doesn't explain why they didn't implement a new way to do this!) removed starting with it.

What exactly IS involved with using an old kernel?  This sounds like more work than installing an older ubuntu release; at least I know how to do that already.  Or do I misunderstand?

I'm going to try to frequency scaling first, because that sounds like I should be able to do it easily and quickly.    

And, yes, I do have an i6 chip or something--why does that keep temperature reporting from working?!  This stuff is insane!  And how did a bug like frying people's laptops get overlooked with the Lucid release?  I'm just floored.

All I want is a laptop that can stay turned on for more than fifteen minutes even in this terrible weather. What would you do if you were in my shoes and the frequency scaling thing doesn't work?  Extremely busy studying, not so very experienced with configuring any of this stuff, and without a local ubuntu expert to help if I really screw things up?

---

### Post by luismgl on 2010-09-01
I'm experiencing the same overheating problems with my laptop, actually I posted myself a topic about it, but it was a rather long time ago. Here are the links if you want to take a look at them: 
[http://ubuntuforums.org/showthread.php?t=1509013](http://ubuntuforums.org/showthread.php?t=1509013)
[http://ubuntuforums.org/showthread.php?t=1509832](http://ubuntuforums.org/showthread.php?t=1509832)

I have a core i3 computer, Ive tried minimizing the cpu's frequency, but that didn't help enough, barely noticeable to be honest. the wake-ups per second are, for sure, the cause of this overheating and poor battery life, I went from 3h using win 7 to 1h20mins with ubuntu 10.04

I'm rather curious about this changing kernels, anyone tried it yet? I'll take a look at the links provided by JedMeister.[URL="http://ubuntuforums.org/member.php?u=414226"]
[/URL]

---

### Post by JedMeister on 2010-09-01
> **karasuman said:**
> Is running Lucid with a different kernel as simple as selecting an older kernel from the list when I power up the laptop?
AFAIK it may be if you did an inplace upgrade from Karmic (ie not a clean install), although I can't confirm that. If you have a kernel that starts with 2.6.31 in the list then its a Karmic one, give it a try. If you did a clean install then all the kernels available from the GRUB screen will all be Lucid (2.6.32) kernels so will all have the bug (assuming that may be your problem).

> **karasuman said:**
> What exactly IS involved with using an old kernel?  This sounds like more work than installing an older ubuntu release; at least I know how to do that already.  Or do I misunderstand?
The second link in the quote I provided in my first post has clear instructions on how to install the Karmic kernel in Lucid - fairly straightforward and easy - no kernel compiling required. (For convenience [here]("http://ubuntuforums.org/showpost.php?p=9388329&postcount=48") it is again). 

It's as simple as downloading the kernel .deb and installing from the commandline. Once installed, you simply choose that kernel from the GRUB screen when booting - any problems, you can always reboot back into a Lucid kernel. I haven't tried it myself (I've stuck with Karmic on portables and left Lucid as is on desktops) but I can't see any issues with it other than the kernel will not receive auto updates. That post is 3 months old and there has only been one update since then so that's probably not a real issue. On that note, rather than downloading the Karmic kernel noted in that post (2.6.31-21) use the latest one ([2.6.31-22]("http://packages.ubuntu.com/karmic-updates/i386/linux-image-2.6.31-22-generic/download")).

Before you start mucking around with that though, it's probably worth checking that that bug is your problem (although TBH considering you have an Intel chip I'm 99% sure it is). Open powertop (*sudo powertop* - you may need to install it: *apt-get install powertop*)and check for excessive numbers beside "[kernel scheduler] Load balancing tick" (it varies but anything much above 80-90 wakeups/sec on battery power is definitely excessive IMO).

Powertop is a very useful tool to assist laptop owners to reduce heat & increase battery life (generally the causes of excessive power usage and excessive heat generation are one and the same).

> **karasuman said:**
> And how did a bug like frying people's laptops get overlooked with the Lucid release?  I'm just floored.I'm with you on that one, especially for an LTS. From what I've read the upstream kernel team are working on it. I just hope the Ubuntu kernel team backport the fixes to Lucid kernel once they are released. I guess most of the kernel developers must either use desktops or live in cold climates and consider it a feature!?

---

### Post by TBABill on 2010-09-02
I'm not sure why, by default, machines run so hot. Just opening video clips will send some computers up into the 80+C range, which is dangerously hot for electronics and the mechanical hard drives. I was able to get my machine down into the 50s/60s using the steps I had listed previously but I am going to look further into powertop as well to see if I can take additional steps.
 
Freq scaling and proprietary video drivers were what saved me. I hope they do for you as well.
 
If you can't solve the heat issue quickly, perhaps try other distros, but specifically those using a different kernel if you believe kernel performance or configuration to be part of the issue. I run several distros so I can compare various aspects of performance. PCLinuxOS is currently on 2.6.33 and openSUSE is on 2.6.34 (I think) so those would allow you to compare, although you mentioned even installing an older Ubuntu is not in your interest.
 
Can you run Windows? Grad school and your time right now are far more important than ideology of free/open source versus MS. Windows, in my experience, always runs cooler unless you have a physical problem (which you most likely do not). It's the "safe way" to protect your machine in the short term if you have the ability and interest to do so.

---

### Post by bobcollard on 2010-09-02
Linux Mint is currently using 2.6.32-24-generic Kernel.  As I wrote earlier, cooler.

---

### Post by JedMeister on 2010-09-02
> **bobcollard said:**
> Linux Mint is currently using 2.6.32-24-generic Kernel.  As I wrote earlier, cooler. Are you running an Intel Atom/C2D/C2Q/i chip? From what I've read, this bug doesn't affect AMD chips or older Intels. If you are using a newer Intel chip and it doesn't suffer this bug then we really need Mint to pass the custom kernel patches they've applied back upstream. AFAIK this is an upstream 2.6.32 kernel bug - _not_ an Ubuntu one. It definitely affects Debian and I thought all distros based on it running a 2.6.32 kernel (Ubuntu and Arch - and I would've thought Mint too). If it doesn't affect Mint then they must have applied a kernel patch which fixed it. If we can find out what it is then we can get it fixed in Ubuntu (and Debian/Arch/etc too). AFAIK the bug still exists in the current Maverick (2.6.35) kernel (although I've heard its a little better). The upstream kernel team are apparently working on it but unfortunately it doesn't seem to be a high priority for them.

> **TBABill said:**
> I run several distros so I can compare various aspects of performance. PCLinuxOS is currently on 2.6.33 and openSUSE is on 2.6.34 (I think) so those would allow you to compare,...If you have the inclination, perhaps you could use Powertop (assuming its available for them?) to compare PCLinuxOS & OpenSUSE kernel load balancing ticks (it may be called something slightly different - it is in Debian). I wonder if there is a significant reason that neither of them are using the 2.6.32 kernel?

**_Back to the issue at hand..._**
> **TBABill said:**
> Can you run Windows? Grad school and your time right now are far more important than ideology of free/open source versus MS. Windows, in my experience, always runs cooler unless you have a physical problem (which you most likely do not). It's the "safe way" to protect your machine in the short term if you have the ability and interest to do so.I wish I didn't, but given the circumstance I have to agree with you.

---

### Post by bobcollard on 2010-09-02
> Are you running an Intel Atom/C2D/C2Q/i chip?No, see screen shots for Info from System Profiler:
As an added note I ran Sabayon 5.3 with 2.6.35 Kernel and it showed 10 degrees hotter Fahrenheit for my pair of processors.

---

### Post by CPL2010 on 2010-09-02
Buy a can of air, take the heat sink off and blow the dust bunnies out of the grill and the fan.

Dell is famous for refurbing their laptops, a side from the poor/tight grill configuration, they are great systems.

Another think to do is to remove the memory and give it the air treatment.

To be blunt, people should be cleaning their laptops with air once a month.  A desktop is 6 months, a lappy is once a month because of design issues

---

### Post by luismgl on 2010-09-02
Im afraid this issue is bigger than dust in the fan. A lot of us have had it, coincidentally all in laptops and most of them with the cpu's already referred. Also I think cleaning a laptop's fan every month seems a bit excessive, I reckon every 3 months should be enough

---

### Post by TBABill on 2010-09-02
Just a note on CPU frequency scaling. Save some trouble, right click the top panel, install the CPU freq scaling applet, left click, select your setting and enjoy. Even easier than my previous post using the terminal to configure.

---

### Post by JedMeister on 2010-09-03
> **bobcollard said:**
> No, see screen shots for Info from System Profiler:
As an added note I ran Sabayon 5.3 with 2.6.35 Kernel and it showed 10 degrees hotter Fahrenheit for my pair of processors.Thanks bobcollard. Perhaps I should have looked at your sig - DOH! Thanks for the clarification and extra info though!

---

### Post by bobcollard on 2010-09-03
> **JedMeister said:**
> Thanks bobcollard. Perhaps I should have looked at your sig - DOH! Thanks for the clarification and extra info though!
The siggy is for general info, when people ask for specifics, I am ready to comply.  Hope this helps.

---

### Post by luismgl on 2010-09-03
could this kernel issue be fixed in the new 10.10 coming out in october?

edit: just noticed that the 10.10 is coming out on the 10.10.10 xD

---

### Post by bobcollard on 2010-09-03
> **luismgl said:**
> could this kernel issue be fixed in the new 10.10 coming out in october?

edit: just noticed that the 10.10 is coming out on the 10.10.10 xD
Since the Kernel issue is affecting more than one Distro the answer is no.  That is unless Ubuntu learns something about how to fix the kernel which comes from outside it's control.  So far I have only found Linux Mint to run cooler.  I've been distro hopping for a year now.  I have a drawer full of disks and very little to show for it, except knowledge of what works on my own computer.  I try to help others, FWIW.

---

### Post by luismgl on 2010-09-04
does this happen in both 32 and 64 bit architecture

---

### Post by JedMeister on 2010-09-04
AFAIK it affects both 32 & 64 bit kernels and currently still affects the beta Maverick kernel (they seem to have made some improvements though - still haven't fixed this bug).

If you have a read on the bug report (link in my first post) you;ll see there's a fair did of community effort going into trying to find a fix for it - and they're having some limited success. If you want to help em out there's a PPA with a number of Maverick kernels with different patches applied (you can try it in Lucid - no need to upgrade your whole system)

---

### Post by luismgl on 2010-09-07
Wakeups-from-idle per second : 155.4    interval: 3.0s
no ACPI power usage estimate available

Top causes for wakeups:
  27.0% ( 85.0)   [kernel scheduler] Load balancing tick
  23.8% ( 75.0)   [ehci_hcd:usb1, ath9k] <interrupt>
  16.9% ( 53.3)   USB device 1-1.1 : USB Multi-Smart Mouse (MLK)
   7.5% ( 23.7)   [i915] <interrupt>
   5.3% ( 16.7)   USB device 1-1.5 : USB2.0-CRW (Generic)
   4.8% ( 15.0)   [kernel core] hrtimer_start (tick_sched_timer)

after turning on computer I went to powertop and this is how it was.
number of wakeups is way too high for idle

---

### Post by Imizael on 2010-09-08
I can confirm on a Dell Inspiron 1564 running Maverick 64-bit that the problem exists.  Windows 7 barely runs the fan at an audible level at idle and close-to-idle, but 10.10 sits the fan at a very audible level 100% of the time.  Sensors is unreliable as stated earlier in the thread.  Powertop reports a rather high wakeups rate, although I don't have the value right now-- I'll edit my post later to give values.

Battery in Win7 lasts a good 3.5-4 hours if I'm conservative with CPU usage and keep screen low.  10.10 reports less than an hour of time off a full battery.  Here's hoping they get this fixed soon-- I'd really like to switch to Ubuntu as my primary OS on this laptop, but killing my battery in an hour or less is not an option...

---

### Post by inso_741 on 2010-09-08
what about the new i5, i3 based notebooks? do they have the same problem?
and does optimus work??

---

### Post by luismgl on 2010-09-08
> **inso_741 said:**
> what about the new i5, i3 based notebooks? do they have the same problem?
and does optimus work??


my notebook has a core i3 processor, and as you can see, I have the same problems.
My fan is constantly working, wakeups through the roof and over heating.

---

### Post by JedMeister on 2010-09-22
> **inso_741 said:**
> what about the new i5, i3 based notebooks? do they have the same problem?
and does optimus work??AFAIK this kernel bug affects pretty much all Intel processors from Core2Duo on, including Core2Duo (obviously), Core2Quad, i3, i5 & i7 as well as all Atom processors (even the single core ones). Some of the later model Celerions fall into this category too (although not the older ones). I haven't tested it but I am yet to hear of an AMD system with the same issues. So although this isn't Intel's fault (it's a kernel bug, not a hardware fault) the only real way to avoid it is to chose a computer with an AMD chip (or not use Linux). If you are considering buying an AMD system on this basis alone, please confirm it before you spend your cash!

Must admit that I'm sort of surprised that Intel aren't pushing the kernel team to fix this.

I don't even know what Optimus is (something to do with nVidia or something?), let alone if it works!

---

### Post by The Real Pelana on 2010-09-22
It seems all of us are getting the same values as for temp1. And Im just running Chrome.

marco@Marco-netbook:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)


how critic would be having the hd running this hot?

marco@Marco-netbook:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD2500BEVS-00UST0: 45°C

I dont want my Atom processor to meltdown. Still gonna try the Karmic kernel, if that doesnt work im planning to switch to Mint.

---

### Post by The Real Pelana on 2010-09-22
Hello once again:

I did install the Karmic kernel and heres the sensors and hddtemp:

marco@Marco-netbook:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  

marco@Marco-netbook:~$ sudo hddtemp /dev/sda
[sudo] password for marco: 
/dev/sda: WDC WD2500BEVS-00UST0: 33°C
marco@Marco-netbook:~$ 

It seems that my works cooler than before Karmic.

@bobcollar still hesitating about Mint but ill keep it as an option. Thanks for the tip.

---

### Post by The Real Pelana on 2010-09-22
> **The Real Pelana said:**
> Hello once again:

I did install the Karmic kernel and heres the sensors and hddtemp:

marco@Marco-netbook:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  

marco@Marco-netbook:~$ sudo hddtemp /dev/sda
[sudo] password for marco: 
/dev/sda: WDC WD2500BEVS-00UST0: 33°C
marco@Marco-netbook:~$ 

It seems that my works cooler than before Karmic.

@bobcollar still hesitating about Mint but ill keep it as an option. Thanks for the tip.



Forgot to mention that Im running Lucid in an Acer Aspire One Atom 1Ghz 1Gb ram 250Gb hd.

---

### Post by luismgl on 2010-10-21
anybody tried 10.10 netbook edition lately??

---

### Post by rawlins02 on 2011-02-18
> sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8 C  (crit = +127.0 C)                  
temp2:       +80.0 C  (crit = +85.0 C)


Should I be concerned about 80 C?  I also have high wakeups from load balancing tick. Quite amazing that this bug has not been fixed. The last post in the bug report, from 02-09-2011:

[https://bugzilla.redhat.com/show_bug.cgi?id=635813](https://bugzilla.redhat.com/show_bug.cgi?id=635813)

says:

"Reported fixed by the original reporter. If you're seeing high wakeup rates on an otherwise idle system (ie, you're not getting any wakeups from i8042 or userspace processes), please open a new bug per machine."

Not sure how to interpret all this...

---

### Post by inso_741 on 2011-04-09
found a great way to undervolt your processor...you dont even have to compile a custom kernel now everything is already available...here's the [tutorial]("http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/")

---

