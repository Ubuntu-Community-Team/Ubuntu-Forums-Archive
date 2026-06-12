---
title: "Just upgraded board to 64 bit and doesn't recognize all the memory"
date: 2012-03-16
forum: General Help
---

### Post by glennc on 2012-03-16
Hello,
  I have been running Ubuntu 11.10 on my old Acer Celeron box. Yesterday I cobbled together an athlon X2 +6000 system with 4 GBs of ram. I downloaded and installed 11.10 64 bit and it seens to be runnning well. But when I go to system info the memory is noted as 1.7 GBs. Did I do something wrong or did I miss an install option. Totally lost at this time and would appreciate any help, information. Thanks in advance!
Glenn

---

### Post by pqwoerituytrueiwoq on 2012-03-16
shared video ram?
which is probably 300mb
one stick of ram is probably bad or not plugged in all the way (ram usually has a lifetime warranty)
switch the ram sticks around (2 sticks of 2gb i assume) and see if it still boots if it does the ram is good and it is the ram slot on the motherboard that is bad

run [FONT=Courier New]uname -m[/FONT] to verify you are running 64bit but even it it were 32bit you should see over 3gb

---

### Post by Bucky Ball on 2012-03-16
Did you just put the RAM in? If so, a stick may be slightly unseated (presuming you have 2x2Gb). Is it new RAM? If so, this sometimes needs to be rubbed with an eraser (believe it or not) where it slips into the RAM slot. 

Try switching off, unplugging and pulling out a stick, boot up again and see if you have RAM. If not, the stick that's in there is the one to investigate, and vice versa, if you follow. ;)

> **pqwoerituytrueiwoq said:**
> 
one stick of ram is probably bad


Possibly, or may just need a little gentle persuasion. ;)

---

### Post by Helen McCall on 2012-03-16
Hi Glenn,

Have you checked in your motherboard manual which sockets to place your RAM. If you place the sticks in the wrong banks then your linux kernel will have difficulty finding them. It looks like it has only found one 2Gig stick.

---

### Post by glennc on 2012-03-16
> **pqwoerituytrueiwoq said:**
> shared video ram?
which is probably 300mb
one stick of ram is probably bad or not plugged in all the way (ram usually has a lifetime warranty)
switch the ram sticks around (2 sticks of 2gb i assume) and see if it still boots if it does the ram is good and it is the ram slot on the motherboard that is bad

run [FONT=Courier New]uname -m[/FONT] to verify you are running 64bit but even it it were 32bit you should see over 3gb

Hello and thanks for the response! Did as you suggested and it say x86_64,
that's 64 bit correct? I am sharing video ram, don't know how much,but I wouldn't think it was 3.3 GBs...
Glenn

---

### Post by glennc on 2012-03-16
> **Bucky Ball said:**
> Did you just put the RAM in? If so, a stick may be slightly unseated (presuming you have 2x2Gb). Is it new RAM? If so, this sometimes needs to be rubbed with an eraser (believe it or not) where it slips into the RAM slot. 

Try switching off, unplugging and pulling out a stick, boot up again and see if you have RAM. If not, the stick that's in there is the one to investigate, and vice versa, if you follow. ;)



Possibly, or may just need a little gentle persuasion. ;)

Howdy,
  I ran the ram in 32 bit which was previously installed. Didn't notice the Ram as I was under the impression that the 32 bit would recognize it.
I have 4 ram slots. 1st 2 are one color, second two are a different color,
I placed the ram in the 1st two slots. Does this matter? I will check the seating again!
Glenn

---

### Post by glennc on 2012-03-16
> **Helen McCall said:**
> Hi Glenn,

Have you checked in your motherboard manual which sockets to place your RAM. If you place the sticks in the wrong banks then your linux kernel will have difficulty finding them. It looks like it has only found one 2Gig stick.

I am unsure of this dual channel stuff so I didn't put one chip in the 1st slot and the 2nd chip in the 3rd slot. They are in 1 and 2 slots. Does this matter? Thanks for your help
Glenn

---

### Post by pqwoerituytrueiwoq on 2012-03-16
depends on the board check your manual or post the model number and ask us to look it up
on my board the second 2 slots (slots 3 and 4) are blue the blue slots are better for overclocking on my board

---

### Post by glennc on 2012-03-16
> **pqwoerituytrueiwoq said:**
> depends on the board check your manual or post the model number and ask us to look it up
on my board the second 2 slots (slots 3 and 4) are blue the blue slots are better for overclocking on my board


Hello,
  Hadn't noticed before but the bios was showing only 2GB. Put the 2nd ram chip in the 3rd Slot and the bios now shows 4 GB. And Ubuntu shows 3.4 GB, I have an onboard video which shares memory. This sounds better doesn't it??
Thanks for your time!
Glenn

---

### Post by 3177 on 2012-03-16
switching your system to 64 bit when you only have 4gigs ram isn't necessary. Unless you Need to switch to 64 bit I wouldn't recommend it.
I still use 10.04 32 bit on a 4core, 4gig machine, no problems.

I've read the other posts and it seems to me that you are having a problem with a bank in your motherboard. An easy way to test this is by inserting only one stick of ram into 1 slot, starting the computer to make sure its being read. Then switch the stick to the other bank.
Obviously if it doest pick it up from one bank you need a new motherboard. 

However if it does, it means that you are most likely using 2 types of ram that are incompatible.

---

### Post by pqwoerituytrueiwoq on 2012-03-16
> **glennc said:**
> Hello,
  Hadn't noticed before but the bios was showing only 2GB. Put the 2nd ram chip in the 3rd Slot and the bios now shows 4 GB. And Ubuntu shows 3.4 GB, I have an onboard video which shares memory. This sounds better doesn't it??
Thanks for your time!
Glennsounds more appropriate the manual for your motherboard will tell how to install your dimms if you care to read it   

[http://i.imgur.com/VVMXK.png](http://i.imgur.com/VVMXK.png) - that is for my board (asus m4a79xdt evo)  

i think 3.4gb is the 32bit limit unless you use a pae kernel, but you are using a 64bit OS so it must be 700mb video ram

---

### Post by glennc on 2012-03-16
> **3177 said:**
> switching your system to 64 bit when you only have 4gigs ram isn't necessary. Unless you Need to switch to 64 bit I wouldn't recommend it.
I still use 10.04 32 bit on a 4core, 4gig machine, no problems.

I've read the other posts and it seems to me that you are having a problem with a bank in your motherboard. An easy way to test this is by inserting only one stick of ram into 1 slot, starting the computer to make sure its being read. Then switch the stick to the other bank.
Obviously if it doest pick it up from one bank you need a new motherboard. 

However if it does, it means that you are most likely using 2 types of ram that are incompatible.

Thanks for the info. The ram is a paired set that came with the board. It is now showing 4 GB of Ram in the BIOS and 3.7 in the sysinfo. Is it working??
Thanks
Glenn

---

### Post by 3177 on 2012-03-16
Your system is now as it sould be.
My sysinfo shows the same 3.7.
A PAE Kernel can be used to get the extra .3

---

### Post by glennc on 2012-03-16
> **3177 said:**
> Your system is now as it sould be.
My sysinfo shows the same 3.7.
A PAE Kernel can be used to get the extra .3


Thanks for your help! I don't know what a PAF kernel is, but the board is an MSI KA780G. It is running 64 bit, it appears that this is not necessary, is it at all beneficial? I will try and download the manual and check on the use of the memory slots. The chips are the same type and now they are both recognized, so I would think that means that both chips are functioning in my limited experience.
Open for any suggestions or opinions. Appreciate your time!
Glenn

---

### Post by pqwoerituytrueiwoq on 2012-03-16
the pae kernel is a easy way to use more ram on a 32 bit but not as efficientally as 64bit can use it
from your [manual](http://download2.msi.com/files/downloads/mnu_exe/E7551v1.0.zip):
[http://i.imgur.com/VpJGO.png](http://i.imgur.com/VpJGO.png)

---

### Post by 3177 on 2012-03-16
the only advantage 64 bit systems have over 32 bit systems is of course 64 bit programs. But 64 bit systems need to emulate 32 bit software. So unless you have a specific 64 bit application you need to use, its a waste of time and hardware. 

Example:
My system monitor running 11.10 64 bit says its using 752Mb ram to run the system.
My same system running 11.10 32 bit uses a mere 154Mb.
Same hardware, but I dont use 64 bit applications, so... you get the picture.

---

### Post by glennc on 2012-03-16
> **pqwoerituytrueiwoq said:**
> the pae kernel is a easy way to use more ram on a 32 bit but not as efficientally as 64bit can use it
from your [manual](http://download2.msi.com/files/downloads/mnu_exe/E7551v1.0.zip):
[http://i.imgur.com/VpJGO.png](http://i.imgur.com/VpJGO.png)

Hello and thanks for your knowledgeable assistance. According to the manual page you posted, I have them in, incorrectly. Yet they show 4GB in the BIOS now. Well, I think you gentlemen have me convinced to reload Ubuntu 32 bit, so I'll play with the chips some more. I don't have any 64 bit programs. I use the cobbled up one as my backup. Fingers crossed, here I go again.
Appreciate your time!
Glenn

---

### Post by glennc on 2012-03-16
> **3177 said:**
> the only advantage 64 bit systems have over 32 bit systems is of course 64 bit programs. But 64 bit systems need to emulate 32 bit software. So unless you have a specific 64 bit application you need to use, its a waste of time and hardware. 

Example:
My system monitor running 11.10 64 bit says its using 752Mb ram to run the system.
My same system running 11.10 32 bit uses a mere 154Mb.
Same hardware, but I dont use 64 bit applications, so... you get the picture.

You have convinced me, I am going to reload Ubuntu 11.10 32 bit.
Wish me luck!! Thanks
Glenn

---

### Post by QIII on 2012-03-16
The advice on 32 vs 64 bit is somewhat misinformed.  There are substantial benefits to using a 64 bit OS if you already have the machine architecture, not the least of which is that 64 bit is the current industry standard in software.

If you have a 32 bit machine and 32 bit OS, with 32 bit applications that suit your needs, then there may be no compelling reason to rush out and buy new hardware.

However, in the last couple of decades things have gone from 8 to 16 to 32 to 64 bit architectures and the holdouts have always found themselves left in the dust.

You have a 64 bit machine.  Use a 64 bit OS.

---

### Post by pqwoerituytrueiwoq on 2012-03-16
> **glennc said:**
> Hello and thanks for your knowledgeable assistance. According to the manual page you posted, I have them in, incorrectly. Yet they show 4GB in the BIOS now. Well, I think you gentlemen have me convinced to reload Ubuntu 32 bit, so I'll play with the chips some more. I don't have any 64 bit programs. I use the cobbled up one as my backup. Fingers crossed, here I go again.
Appreciate your time!
Glenn
if they were correct in the 1st place the slot could be dead  you can try both in the other slot
as of now you have 4gb or ram but no dual channel if you are using slots 1 and 3

i would stick with 64bit most apps are native 64bit now days (including firefox) it should run a tad faster than its 32bit version
64bit apps tend to be larger than there 32bit version

---

### Post by glennc on 2012-03-16
> **QIII said:**
> The advice on 32 vs 64 bit is somewhat misinformed.  There are substantial benefits to using a 64 bit OS if you already have the machine architecture, not the least of which is that 64 bit is the current industry standard in software.

If you have a 32 bit machine and 32 bit OS, with 32 bit applications that suit your needs, then there may be no compelling reason to rush out and buy new hardware.

However, in the last couple of decades things have gone from 8 to 16 to 32 to 64 bit architectures and the holdouts have always found themselves left in the dust.

You have a 64 bit machine.  Use a 64 bit OS.

I have steadfastly changed my mind again. It is going to be a 64 bit Ubuntu Destop. Thanks for you help in pointing out the benefits and such.
Glenn

---

### Post by glennc on 2012-03-16
> **pqwoerituytrueiwoq said:**
> if they were correct in the 1st place the slot could be dead  you can try both in the other slot
as of now you have 4gb or ram but no dual channel if you are using slots 1 and 3

i would stick with 64bit most apps are native 64bit now days (including firefox) it should run a tad faster than its 32bit version
64bit apps tend to be larger than there 32bit version

I believe I'm loosing clarity on this issue. Heres what I did, I put the one chip in the slot 1 and the bios showed 2 GB. Previously I had chip one in slot one and chip two in slot two. This gave me according to the bios 2 GB. I put the second chip in the first slot only and the bios showed 2GB. Now here is were it gets weird. With chip two in slot one and chip one in slot two, the thing wouldn't even come up. So I put chip one in slot 3 and it shows 4GBs again. This is about all I can handle for today. Tried to load Windows8 preview on the machine in the interim with no luck. So I am going to load it back with 64 Bit Ubuntu and call it a day. Who knows what tomorrow will bring. Thank you for your help. I know I can't explain it!!!
Cheers
Glenn

---

### Post by grahammechanical on 2012-03-16
Hi

Have a rest. Let the brain ease off a bit and when you are ready put aside all the suggestions about 32bit or 64bit. That is a distraction from the main task. Just think about getting the two RAM chips in the right slots. 

Look again at the image that was provided in a link.

If you put one chip in slot DIMM_A1 and one chip in slot DIMM_A2 you should show 4GB but they will be in single channel mode. Data transfer will be slower than in dual channel mode.

So, you have a choice.

Put one chip in slot DIMM_A1 and the other chip in slot DIMM_B1

or 

Put one chip in slot DIMM_A2 and the other chip in slot DIMM_B2

This should give you 4GB in dual channel mode.

The slots are in pairs so as you have paired RAM chips you keep them in pairs.

By splitting the chips across the two pairs of slots you got 4GB alright but it would be in single channel mode.

The cause of this:

> With chip two in slot one and chip one in slot two, the thing wouldn't even come up

Could be down to a failure to seat one of the chips correctly. This can easily happen.

Try again with both chips in the first bank of two slots. If that does not give you 4GB then try again with both chips in the second bank of slots.

It should not matter whether you think of one chip as chip 1 and the other as chip 2. It should not make any difference which order you put these two chips in. Neither one is the first. Neither one is the second.

Be assured in your mind that if the BIOS is seeing 4GB RAM and you install 64bit Ubuntu then it will see 4GB (or just under). The 64bit Ubuntu kernel is designed to see more than 4GB of RAM, much more than 4GB.

The 32bit kernel was not originally designed to see up to 4GB. It had to be extended in some way to see up to 4GB and beyond.

Regards,

---

### Post by glennc on 2012-03-16
> **grahammechanical said:**
> Hi

Have a rest. Let the brain ease off a bit and when you are ready put aside all the suggestions about 32bit or 64bit. That is a distraction from the main task. Just think about getting the two RAM chips in the right slots. 

Look again at the image that was provided in a link.

If you put one chip in slot DIMM_A1 and one chip in slot DIMM_A2 you should show 4GB but they will be in single channel mode. Data transfer will be slower than in dual channel mode.

So, you have a choice.

Put one chip in slot DIMM_A1 and the other chip in slot DIMM_B1

or 

Put one chip in slot DIMM_A2 and the other chip in slot DIMM_B2

This should give you 4GB in dual channel mode.

The slots are in pairs so as you have paired RAM chips you keep them in pairs.

By splitting the chips across the two pairs of slots you got 4GB alright but it would be in single channel mode.

The cause of this:



Could be down to a failure to seat one of the chips correctly. This can easily happen.

Try again with both chips in the first bank of two slots. If that does not give you 4GB then try again with both chips in the second bank of slots.

It should not matter whether you think of one chip as chip 1 and the other as chip 2. It should not make any difference which order you put these two chips in. Neither one is the first. Neither one is the second.

Be assured in your mind that if the BIOS is seeing 4GB RAM and you install 64bit Ubuntu then it will see 4GB (or just under). The 64bit Ubuntu kernel is designed to see more than 4GB of RAM, much more than 4GB.

The 32bit kernel was not originally designed to see up to 4GB. It had to be extended in some way to see up to 4GB and beyond.

Regards,

Hello and thanks,
   I will read this again tomorrow, in depth, after coffee and try again. My Ubuntu which is now up and running 64 bit is showing 3.6 GB of RAM. Since you've indicated that 64 Bit should show the full amount or more if installed, I am sharing memory with the onboard video, so I will assume that is why there is a difference. Tomorrow I will en-devour to persevere! I do want to run dual channel. 
Glenn

---

### Post by pqwoerituytrueiwoq on 2012-03-16
for tomorrow
currently you have slots 1 and 3 in use and have 4gb
when you use 1 and 2 you are missing 2gb of ram
so unless you had the ram not plugged into slot 2 properly (i assume you have tried this 2 times)
it would mean 1 of 2 things
A the slots is dead
B the slot needs cleaning (contact cleaner not contact lens btw)
you can try slots 3 and 4 with your ram and if you can see 4gb then you will be using it in dual chanel

---

### Post by Bucky Ball on 2012-03-16
Please mark thread as 'Solved' to help others if your original issue is solved (missing RAM).

64bit is about utilising the CPU to best advantage (dual-core and above = 64bit), not really about RAM.

---

### Post by glennc on 2012-03-16
> **Bucky Ball said:**
> Please mark thread as 'Solved' to help others if your original issue is solved (missing RAM).

64bit is about utilising the CPU to best advantage (dual-core and above = 64bit), not really about RAM.

Hello Bucky Ball,
    It is premature as noted in the thread as to whether the problem is solved or not. When it is I will certainly try to remember to mark it as such. Thanks for the reminder
Glenn

---

