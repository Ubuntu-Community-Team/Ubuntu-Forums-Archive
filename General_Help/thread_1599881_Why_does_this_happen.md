---
title: "Why does this happen?"
date: 2010-10-18
forum: General Help
---

### Post by cyberjar09 on 2010-10-18
I am using Maverick Meerkat on my office computer and I dont know why this is happening to my desktop after prolonged usage. Please help. Screenshot attached.

Also I have detected that when I open too many chrome windows the computer just hangs! I have 1 Gb of RAM, this should not be happening. Is there any way for me to optimise ubuntu for my desktop's hardware 

thanks again.

---

### Post by Rubi1200 on 2010-10-18
Hi,
couple of things to try:

1. turn off desktop effects (Compiz)

2. check the .xsession-errors file for any indication as to why this is happening

Finally, what graphics card do you have installed?

---

### Post by 3Miro on 2010-10-18
Chromium is a memory hog. Firefox tends to be more conservative. Still, it shouldn't crash like that. Do you have swap setup properly. 

Go to System -> Admin -> System Monitor and check to see how much Swap you have. Also, try to keep track of the RAM usage when it crashes.

---

### Post by cyberjar09 on 2010-10-19
> **Rubi1200 said:**
> Hi,
couple of things to try:

1. turn off desktop effects (Compiz)

2. check the .xsession-errors file for any indication as to why this is happening

Finally, what graphics card do you have installed?

1. in compiz config settings manager i hav switched off 'animations' and 'fading windows' in the "effects" tab. anything else I need to disable?

2. where is the .xsession-errors file located? Next time such a problem reoccurs, ill check the file and post it back here for you to analyze.

---

### Post by cyberjar09 on 2010-10-19
> **3Miro said:**
> Chromium is a memory hog. Firefox tends to be more conservative. Still, it shouldn't crash like that. Do you have swap setup properly. 

Go to System -> Admin -> System Monitor and check to see how much Swap you have. Also, try to keep track of the RAM usage when it crashes.

My swap shows 1Gb of space assigned. but my RAM usage is pretty high even as am typing this now i have a few windows and tabs open and my ram usage is 75% of 1Gb.

---

### Post by cyberjar09 on 2010-10-19
Also, I am using an IBM ThinkCentre desktop PC which is pretty old. It has a small speaker on the front of the chassis but it does not seem to work in Ubuntu. Where can I find out the exact model so that i can install the driver?

---

### Post by mastablasta on 2010-10-19
> **cyberjar09 said:**
> 1. in compiz config settings manager i hav switched off 'animations' and 'fading windows' in the "effects" tab. anything else I need to disable?
 
 
Try turning off all desktop effects?! not in compiz config but on desktop configuraiton i believe.
 
you still didn't answer to:
what graphics card do you have?

---

### Post by mastablasta on 2010-10-19
> **cyberjar09 said:**
> Also, I am using an IBM ThinkCentre desktop PC which is pretty old. It has a small speaker on the front of the chassis but it does not seem to work in Ubuntu. Where can I find out the exact model so that i can install the driver?
 
it would be better to post this issue in separate thread.
 
 
speaker or beeper?
 
ok let's assume speaker. first check it if is propperly connected to the motherboard.
 
next type > lspci in the terminal and post the output here using the code tags. this command will list your devices.

---

### Post by cyberjar09 on 2010-10-19
> **mastablasta said:**
> it would be better to post this issue in separate thread.
 
 
speaker or beeper?
 
ok let's assume speaker. first check it if is propperly connected to the motherboard.
 
next type  in the terminal and post the output here using the code tags. this command will list your devices.

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751F Fast Ethernet PCI Express (rev 11)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

So this would also help list my graphics option im guessing. If not please tell me the terminal command to list my graphics card .

Thank you.

---

### Post by blueridgedog on 2010-10-19
> **mastablasta said:**
> Try turning off all desktop effects?! not in compiz config but on desktop configuraiton i believe.
 

System, preferences, appearance then the visual effects tab, set to none and see if it changes your results.

---

### Post by cyberjar09 on 2010-10-19
> **mastablasta said:**
> Try turning off all desktop effects?! not in compiz config but on desktop configuraiton i believe.
 
you still didn't answer to:
what graphics card do you have?

where is the desktop configuration option ? 

I have posted the results of lspci in the previous post. That ought to cover my graphics solution. Please let me know if there are any other commands I need to run. 

Thanks.

---

### Post by cyberjar09 on 2010-10-19
> **blueridgedog said:**
> System, preferences, appearance then the visual effects tab, set to none and see if it changes your results.

I have set it to none. And my desktop is back to that same pixellated appearance. I am going to restart now and will report back if thru the course of the next day or two the problem comes back.

---

### Post by Rent_A_Pig on 2010-10-19
It may not be a problem with Ubuntu at all.  What I have noticed is that with older PCs, age is not good for them.   Kinda like people...  You may be a strapping young lad now but just wait till your in your 70's or 80's.  Memory is lost with no explanation as to where it has gone,  energy is more or less non existant, and your parts just don't work like they should...
 
 
In other words,  all the compiz and desktop tweeks may make things better but sooner or later its gonna be best just to pull the plug.   
 
:P

---

### Post by mastablasta on 2010-10-19
```
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```
This is basicly your graphics card. 
 
```

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

```
This is your sound card.
 
> where is the desktop configuration option ? 

 
 
Either like **blueridgedog** said or right click on desktop, select change background and then choose visual effects tab. :-)

---

### Post by cyberjar09 on 2010-10-19
> **mastablasta said:**
>  
Either like **blueridgedog** said or right click on desktop, select change background and then choose visual effects tab. :-)

thanks mastablasta. I have set it to none as specified. I will report back if the problem persists or i will mark the thread as [solved] if the problem goes away.

---

### Post by cyberjar09 on 2010-10-19
So i opened up the cabinet and found the speaker was connected to the mobo. 

The headphone jack works perfectly but I would much prefer if this little speaker got going. 

any ideas?

---

### Post by cyberjar09 on 2010-10-19
> **cyberjar09 said:**
> So i opened up the cabinet and found the speaker was connected to the mobo. 

The headphone jack works perfectly but I would much prefer if this little speaker got going. 

any ideas?

I played around with the sound settings and managed to get the sound working! woohoo! :guitar: 

now the speaker and the headphones both work simultaneously but im ok with that as long as the speaker works..!

---

### Post by Rent_A_Pig on 2010-10-19
> **cyberjar09 said:**
> I played around with the sound settings and managed to get the sound working! woohoo! :guitar: 
 
now the speaker and the headphones both work simultaneously but im ok with that as long as the speaker works..!
 
 
In the same settings there will be a place to turn the headphone jack off just like the speaker was by default..
 
what is the manufacture date on that machine?

---

### Post by cyberjar09 on 2010-10-19
> **Rent_A_Pig said:**
> In the same settings there will be a place to turn the headphone jack off just like the speaker was by default..
 
what is the manufacture date on that machine?

The settings that i toggled are shown in the screenshot attached. No joy on the headphone disabling.

no problem though i really dont mind.

---

### Post by Rent_A_Pig on 2010-10-19
> **cyberjar09 said:**
> The settings that i toggled are shown in the screenshot attached. No joy on the headphone disabling.
 
no problem though i really dont mind.
 
 
Hardware tab maybe?  this is 10.10 correct?

---

### Post by cyberjar09 on 2010-10-22
ok so all the things i have tried till now have not worked ... because I was greeted by this desktop last night .. any ideas?

---

### Post by cyberjar09 on 2010-10-28
no luck ppl ... this is a recurring problem. 

please help me rectify this. 

find screenshot attached.

---

### Post by cyberjar09 on 2010-10-28
Is there no support for this problem im facing? 

What should i try to maybe help resolve the situation because im tired of having to restart everytime this computer decides its time to go amazingly slow...

---

### Post by blueridgedog on 2010-10-28
You have a significant amount of swap space used and I suspect that is is grinding your system to a halt with the graphics degradation is a symptom of the system load.  When the system slows down, what is the output of 

```
iotop
```

I recommend you use Firefox as a browser and keep only one window of firefox open given the system specs you have.

---

### Post by cyberjar09 on 2010-10-28
> **blueridgedog said:**
> You have a significant amount of swap space used and I suspect that is is grinding your system to a halt with the graphics degradation is a symptom of the system load.  When the system slows down, what is the output of 

```
iotop
```

I recommend you use Firefox as a browser and keep only one window of firefox open given the system specs you have.

The command iotop dint seem to end so i took a screenshot while it was running. Please find screenshot attached. 

also, i think the memory is getting flooded with chrome but i was under the impression that chrome is light on the system resources. ???]
:confused:

---

### Post by blueridgedog on 2010-10-28
Based on what I see, your system is IO (input output) bound due to excessive swap space utilization. 

You can do the following to help out:
-Upgrade/increase your system memory
-Run fewer programs (I see you often have two instances of Chrome open, try Firefox and only one instance)
-Eliminate unwanted start up programs (System - Preferences - Start up applications)
-Close windows and program when not in use.

My first recommendation would be to upgrade the memory.

---

### Post by cyberjar09 on 2010-10-28
> **blueridgedog said:**
> Based on what I see, your system is IO (input output) bound due to excessive swap space utilization. 

You can do the following to help out:
-Upgrade/increase your system memory
-Run fewer programs (I see you often have two instances of Chrome open, try Firefox and only one instance)
-Eliminate unwanted start up programs (System - Preferences - Start up applications)
-Close windows and program when not in use.

My first recommendation would be to upgrade the memory.

Ok i will upgrade the RAM. 

Will post back in case the problem persists, or I will mark the thread as solved after some time. 

Thanks.

---

### Post by cyberjar09 on 2010-11-19
works perfectly now..

it would appear it was an issue of old buggy RAM ... changed the RAM out and put in newer chips ... no more problems 

marked SOLVED

---

