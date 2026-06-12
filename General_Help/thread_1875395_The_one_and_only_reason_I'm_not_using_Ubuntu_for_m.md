---
title: "The one and only reason I'm not using Ubuntu for my main Desktop OS"
date: 2011-11-04
forum: General Help
---

### Post by Fred Doolie on 2011-11-04
1.8 Gig AMD (K8?)CPU <--It's 64 bit anyway.
4 Gigs RAM
4 Gig Swapfile for Ubuntu   4 Gig Pagefile.sys for Windows

I love Linux and especially Ubuntu. LOVE IT! But it multitasks terribly on my system. HORRIBLY! If I want to run two instances of Firefox or two Secondlife Viewers or even Firefox and Gimp at the same time the following occurs:

Windows:
App#2 loads up a bit slowly but runs well. App#1 also runs well. Both are useable. Both are a bit slow but not too bad. They stay usable and run together just fine. I can even run three or four heavy duty apps at the same time! They just run a bit slowly.

Ubuntu:
App#2 takes a LOOOOONG time to load and while it does app#1 stops dead. App#1's window turns white. Then #2 comes up white. Both are white for a while. App#1 becomes visible. Then #2's window becomes visible. My entire screen turns white. Then it goes back to normal. They may run for a little while (10 minutes?) but are too SLOOOOOW to be of great use.  Activating #1 cause #2 to turn white. Activating #2 makes #1 white. Trying to run 3 apps makes the system locks up and then reboot. Even with two it will lock up and reboot sooner or later.

Even with one heavy duty app running folder windows open up solid white and take 2-3 minutes to show the icons while the OS just sits there saying "Duuuuh".

Its not just Ubuntu. Every Linux I've tried does this. Ubuntu 11.10 is by FAR the worst offender though. 

If all that could be fixed I'd use Ubuntu as my main OS in a second! Yes I did install graphic drivers (Nvidia). 
-----------------------------------
On my crap-*** 1-Gig RAM Netbook even 11.10 runs like a dream. No black-screen bootup. No loading delays and no white windows/system crashes.

---

### Post by ##Villain on 2011-11-04
> **Fred Doolie said:**
> 1.8 Gig AMD (K8?)CPU <--It's 64 bit anyway.
4 Gigs RAM
4 Gig Swapfile for Ubuntu   4 Gig Pagefile.sys for Windows

I love Linux and especially Ubuntu. LOVE IT! But it multitasks terribly on my system. HORRIBLY! If I want to run two instances of Firefox or two Secondlife Viewers or even Firefox and Gimp at the same time the following occurs:

Windows:
App#2 loads up a bit slowly but runs well. App#1 also runs well. Both are useable. Both are a bit slow but not too bad. They stay usable and run together just fine. I can even run three or four heavy duty apps at the same time! They just run a bit slowly.

Ubuntu:
App#2 takes a LOOOOONG time to load and while it does app#1 stops dead. App#1's window turns white. Then #2 comes up white. Both are white for a while. App#1 becomes visible. Then #2's window becomes visible. My entire screen turns white. Then it goes back to normal. They may run for a little while (10 minutes?) but are too SLOOOOOW to be of great use.  Activating #1 cause #2 to turn white. Activating #2 makes #1 white. Trying to run 3 apps makes the system locks up and then reboot. Even with two it will lock up and reboot sooner or later.

Even with one heavy duty app running folder windows open up solid white and take 2-3 minutes to show the icons while the OS just sits there saying "Duuuuh".

Its not just Ubuntu. Every Linux I've tried does this. Ubuntu 11.10 is by FAR the worst offender though. 

If all that could be fixed I'd use Ubuntu as my main OS in a second! Yes I did install graphic drivers (Nvidia). 
-----------------------------------
On my crap-*** 1-Gig RAM Netbook even 11.10 runs like a dream. No black-screen bootup. No loading delays and no white windows/system crashes.

Wierd on my Dell laptop Ubuntu works extremely well. Seems like a hardware issue.

---

### Post by Rodney9 on 2011-11-04
Try a light weight version of Ubuntu like Lubuntu, you will see a big difference in speed.

---

### Post by gordintoronto on 2011-11-04
Open Terminal, and enter this command:
sudo lshw > myconfig.txt

A few lines in will be the CPU section. Please copy/paste it here.

---

### Post by techvish81 on 2011-11-04
it's an issue with,  nvidia, (search in threads with nvidia keyword)  remove the driver u installed and use what is installed by default,  actually u dont need that driver.

---

### Post by Fred Doolie on 2011-11-05
> **gordintoronto said:**
> Open Terminal, and enter this command:
sudo lshw > myconfig.txt

A few lines in will be the CPU section. Please copy/paste it here.

    *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor 2650e
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.15.2
          slot: Socket AM2
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 201MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
          configuration: cores=1 enabledcores=1 threads=1

---

### Post by Fred Doolie on 2011-11-05
> **techvish81 said:**
> it's an issue with,  nvidia, (search in threads with nvidia keyword)  remove the driver u installed and use what is installed by default,  actually u dont need that driver.

Well, I'll be dipped. I installed a new clean copy of 11.10 and this time did NOT install the "Add New Hardware" Nvidia driver.

Works great. Still a little slow but nowhere NEAR as bad. Now I just get ghosted windows for a few seconds and then everything is fine. No more solid white stuff and lockups. I ran two instances of Secondlife and it worked so well I didn't even get slowdowns in the frames per second on them. WAAAAAAAY BETTER! tytytytyty

I also didn't get the "Window Creation Error" I use to get with Second Life and older Ubuntus until I installed the Nvidia driver. 11.10 must come with a decent one.

Buys you a virtual beer and searches for the fancy screen effects option that USE to be in "Appearance" to see if that works too. Does 11.10 even have it?

---

### Post by gordintoronto on 2011-11-05
Search for "compiz config settings manager" in Software Centre. Warning: I have read that you can break your system with some of the settings, then you need to boot in safe mode, or whatever it's called.

What video adapter is in your computer?

---

### Post by Fred Doolie on 2011-11-05
> **gordintoronto said:**
> Search for "compiz config settings manager" in Software Centre. Warning: I have read that you can break your system with some of the settings, then you need to boot in safe mode, or whatever it's called.

What video adapter is in your computer?

nvidia 6510SE onboard. cheap junk but it does work.

---

### Post by dFlyer on 2011-11-05
I have no problems running multiple applications including the one talked about above. I do a lot of photo editing and things still work smoothly on my dell with 4gig of ram and an a 8 gig swap file. can you provide more information about your system.

---

### Post by Fred Doolie on 2011-11-05
Update: Went back to 11.04.  11.10 is a slow dog and still broken (no offense intended to the Ubuntu team. You guys are great, really).

Digging around shows that Ubuntu automagically installed the older 173 nvidia drivers. "Ubu" knows best. I was breaking my own system by insisting on the CURRENT drivers(1). Hehe I caused my own problems by installing a turbo powered driver on a rubber-band powered graphic card. I didn't even KNOW it installed drivers by itself. I had always seen that "Drivers are available" message and gone to the Add Hardware icon at top right saying "Well, duh! Of course I want hardware drivers". I busted it myself. haha what a clone!
-----------------
(1) Ubuntu Team, How about a pop-up on first boot saying:
Onboard Nvidia sound card detected - current drivers installed.

Onboard Nvidia Graphics card (6510SE) detected - Older drivers for pre-2008 card installed -DO NOT UPDATE!

Blahblahblah detected - Basic temporary drivers installed - Update from your manufacturer's website with proper drivers ASAP.
and so on?

---

### Post by Fred Doolie on 2011-11-06
> **dFlyer said:**
> I have no problems running multiple applications including the one talked about above. I do a lot of photo editing and things still work smoothly on my dell with 4gig of ram and an a 8 gig swap file. can you provide more information about your system.

The problem was the video driver. The current one doesn't work with my on-board card. With the old driver (Nvidia173) installed all is well and I can multitask great.

---

### Post by gordintoronto on 2011-11-06
> **Fred Doolie said:**
> Onboard Nvidia Graphics card (6510SE) detected - Older drivers for pre-2008 card installed -DO NOT UPDATE!

Great suggestion!

I think you could mark this thread as Solved.

---

### Post by Fred Doolie on 2011-11-09
> **Rodney9 said:**
> Try a light weight version of Ubuntu like Lubuntu, you will see a big difference in speed.

"Big" difference?  Try HUGE! I've never seen my system run that quickly before except in Puppy Linux (the OS runs totally in RAM). Guess which buntu is going on my netbook. Using LXDE even gave me a faster frame rate in Secondlife. Windows open pop pop pop, stuff loads very quickly and the system shuts down in 5 seconds.

---

