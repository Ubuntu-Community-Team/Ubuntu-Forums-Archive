---
title: "Segmentation faults since memory upgrade."
date: 2010-02-26
forum: General Help
---

### Post by momist on 2010-02-26
Hi there,

I'm struggling with this problem, and don't know what to test to find the answer.  Since I upgraded my memory to 4GB, I have been getting lots of segmentation faults, but not all the time.  The symptoms are that certain programs just won't run.  For example, Rhythmbox will try to start, showing an entry on the panel saying "Starting Rhythmbox" but then it simply goes away after about 20 seconds.  A re-boot sometimes fixes it, but frequently doesn't.  If I start a terminal (at the moment terminal displays the same symptoms and won't start!) and use that to start Rhythmbox, it returns "segmentation fault" and nothing else.

The memory checks out perfectly with Memtest86+, and I've tried setting the BIOS "memory hole" remapping both on and off.

This is a 2GHz Athlon64 X2 processor (Manchester core) on an Asus A8V motherboard.  The memory is 4 x 1GB Kingston Value Ram of the Asus approved type.  I've set the latency and speed to match the memory, and I'm not over clocking.  I'm running Karmic 64 bit, and it worked flawlessly with only 2GB of memory.

What I will try next is running with only 2GB for a while, using first one pair of SDRAM and then the other pair.

Can anyone suggest what else I could try please?

Thanks,

---

### Post by ajgreeny on 2010-02-26
Why not remove the memory modules one by one, rather than in pairs.  That will show which is the faulty one, if any.

---

### Post by thomas144 on 2010-02-26
I'm no expert, but I may have something to say. If you are running a 32-bit operating system, there's a limit to how much RAM the system can use. If you aren't running the AMD64 version, this might be a problem. But then, I'm just guessing.

---

### Post by ajgreeny on 2010-02-26
> **thomas144 said:**
> I'm no expert, but I may have something to say. If you are running a 32-bit operating system, there's a limit to how much RAM the system can use. If you aren't running the AMD64 version, this might be a problem. But then, I'm just guessing.
This would not normally throw a segmentation fault, it would just not show the extra memory.

---

### Post by momist on 2010-02-26
> **ajgreeny said:**
> Why not remove the memory modules one by one, rather than in pairs.  That will show which is the faulty one, if any.

Sorry, I should have said that this motherboard runs the memory in pairs, to give 64 bit wide access (dual channel memory).  This only works when ALL the cards are identical.  The MoBo handbook doesn't say "matching" RAM, but a lot of discussion on the boards refer to that.  I'm wondering if my memory is not "identical" enough, i.e. not "matching".  They are the same model, but not consecutive serial numbers.

The reliable operation was using a different manufacturer's memory cards which I couldn't get matching ones for to upgrade, so I've bought these Kingston ones via eBay.  Could be they're "iffy" I suppose, despite the good reports from Memtest86+.  

@thomas144, I am running the AMD64 version of Ubuntu.  I'm aware of the limitations of the memory address range, and as I said, this MoBo gets around that with the re-allocation of the "lost" memory to a higher range.  However, I've tried this turned off and turned on, with no improvement.

Currently (since another re-boot) Rhythmbox and terminal work, but some other random programs don't work.  It seems to be different every time I start up.

---

### Post by momist on 2010-02-27
OK, so here's the results.  

The MoBo is capable of supporting 4 x 1GB of memory in 4 slots.  When only 2 slots are used, they have to be the alternate (blue) sockets.
I've removed half the memory, and the system is totally stable.
I've put the other two cards in the same 2 slots, and the system is totally stable.
With all 4 cards installed, the system is unstable, but the degree varies with each boot.

Strangely, it's mainly a small game (Gweled) and Terminal that exhibit the most likely failure, oh and also Rhythmbox as I said before.  Sometimes I can open nearly all the entries on the Accessories menu apart from Terminal, and sometimes very few programs will run.

Can anyone suggest where the problem might lie?  Obviously the memory itself is not at fault.  I can see that it could be a problem with the motherboard, but I suspect it's something more related to Ubuntu AMD64 and my motherboard configuration.

---

### Post by warp99 on 2010-02-27
> Could be they're "iffy" I suppose, despite the good reports from Memtest86+.

They could be mis-labeled which happens all of the time especially if the sticks didn't come in a clam shell package. It does look like it's a mismatch with the memory or a timing issue but it could also be the AMD processor failing to address the upper ranges. I had Abit KV8 board, which also uses a K8T800 Pro chipset. It had a AMD64 +3500 that stated to have random memory issues after about 4 years. I eventually tracked the problem to the processor since the memory error ranges during the extended memtest were exactly the same no matter which stick I used.

---

### Post by momist on 2010-02-27
> **warp99 said:**
>  [snip]  It had a AMD64 +3500 that stated to have random memory issues after about 4 years. I eventually tracked the problem to the processor since the memory error ranges during the extended memtest were exactly the same no matter which stick I used.

Hmmm, I hadn't thought that the processor could be the trouble.  All these bits are 'used' bought off eBay, so anything is possible.  The four sticks of RAM do look very similar, but not quite identical as despite the same labels the chips have different numbers on one stick.  However, even that one is flawless when used with any other stick, the trouble only occurs when all 4 are installed.  I don't think it can be a timing issue, the RAM timings are printed on the labels and are all the same.

I'm starting to think I may sell off these four again, and revert to my other two, which worked OK.  I was only hankering after making the computer 'complete' with a full memory allocation, and avoid any slowing down when handling large images and video files.  To be honest, System Monitor only ever shows 2GB 88% used, even with _lots_ of programs and files open, but then I haven't tried any serious image manipulation yet.  I'm thinking of panorama stitching which is very memory hungry, as it has to slide the images around to get a match, and adjust colour/saturation/contrast at the same time.

Thanks for your thoughts.

---

### Post by psusi on 2010-03-03
Sounds like either overheating or undervoltage.  You can rule out overheating by getting a large house fan and having it blow at the memory.  You can try fiddling with the memory voltage and timing in the BIOS to see if that helps too.

---

### Post by momist on 2010-03-03
> **psusi said:**
> Sounds like either overheating or undervoltage.  You can rule out overheating by getting a large house fan and having it blow at the memory.  You can try fiddling with the memory voltage and timing in the BIOS to see if that helps too.

Thanks for the idea - I've not tried the voltage settings - I'm not sure where to find them but I'll have a look in the BIOS.  I'm sure it's not overheating, as I can replicate the segmentation faults immediately from a cold start, and 18 hours of Memtest with 12 passes shows NO errors.

My other thread on this is at:
 [http://ubuntuforums.org/showthread.php?t=1419231](http://ubuntuforums.org/showthread.php?t=1419231)
where you'll see I've done some experimenting with the memory timings already.

Thanks for the response.

---

### Post by momist on 2010-03-07
OK, so here's the latest.

I have tried the 4GB installed with the memory speed slowed down to DDR333, which is the default setting of the motherboard when 4GB is in use.  (The handbook says to set the speed manually, after testing the memory.)  At first I thought that this had cured the problem, as I no longer get segmentation faults, however, this has resulted in significant corruption of my home directory, and instability in such programs as Firefox and Thunderbird, together with failures of the window manager resulting in loss of control of programs and sometimes a black screen.

It's time to give up on this.  I've had the kind help of someone with much more knowledge and experience of such things, and he can't find the cause of my troubles.

I can't risk any further problems with my data, and have removed the 4GB, which I'll now attempt to sell on.  It seems I will always be stuck at 2GB with this motherboard, which I find very disappointing.  Now I need to start fixing the damage in the home directory, which I suspect will require deleting my user and starting again, as several config files have become corrupted.  Luckily, I don't use Evolution, which I understand in so intertwined with Gnome that I would struggle to retain my emails etc.

I'll not mark this thread solved, as it isn't, but just let it die.

Thanks for looking.

---

