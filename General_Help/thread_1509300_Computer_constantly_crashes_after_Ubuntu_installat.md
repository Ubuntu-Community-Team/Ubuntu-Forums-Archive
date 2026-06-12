---
title: "Computer constantly crashes after Ubuntu installation"
date: 2010-06-14
forum: General Help
---

### Post by charliechip95 on 2010-06-14
We've had a very big problem with our computer chrashing for a while, and I'm not sure if it's Linux Ubuntu that's the problem or not be we'd like some feedback from the experts of this forum. I hope I'm posting this in the right place. :p

So, a while back we had Windows XP on our machine, and it had been running well (as well as XP is capable anyway, ;)), but for some reason it wouldn't boot XP properly and would only allow us to open it in Safe Mode.

We opened up the computer to take the memory chips out and back in, just in case that would help, and the inside was terribly dusty. Also, we have a loose heatsink, and the chip underneath is filled with dust. Not sure what the chip is -- I'll try to get some picture of it pretty soon. Anyway, the inside of the machine obviously wasn't too good.

So, we installed Linux Ubuntu LTS 10.04 on it from a CD to try to fix the booting problem, and this worked -- but now, our computer crashes constantly after turning on. It crashes whatever we're doing -- we can do something light, like Google Chrome, or something heavy, like video editing, and have it crash on us. So it doesn't seem to be a problem with the programs or anything -- I'm guessing it's either an issue with the computer itself or an error with the operating system.

Sometimes we're lucky and can be on the computer for half-hour to and hour and a half, but it's still really bothersome, and will get in the way of any projects that require saving or recording. I'd guess it crashes around 10-20 times a day.

I included a video of it crashing and what it does just in case that could be of any help. Link:

[http://www.youtube.com/watch?v=9UHayH2XskM](http://www.youtube.com/watch?v=9UHayH2XskM)

The screen goes blank for a moment -- shows oddly colored, fragmented bars in the center of the screen (sometimes red, sometimes silver), shows this text:

```
 * Speech-dispatcher configured for user sessions
						     * Starting the Winbind daemo
winbind									    [ OK

* Starting Common Unix Printing System: cupsd				    [ OK

* PulseAudio configured for per-user sessions

 inary formats binfmt-support			* Enabling additional executable

* Checking battery state...						    [ OK
```

and then goes back and forth between not outputting any video and displaying these white bars at the top of the screen. Also, here are some of our computer specs (most of which I found using the Sysinfo program)...

**SYSTEM**
Model: Sony Vaio PCV-2210

**OS**
Release: Ubuntu 10.04 (lucid) 32-bit
GNOME: 2.30.0
Kernel: 2.6.32-22-generic

**CPU**
Vendor: GenuineIntel
CPUs: 1
Model name: Intel(R) Pentium(R) 4 CPU 2.53GHz
Frequency: 2545.553 MHz
L2 cache: 512 KB

**MEMORY**
Memory total: 489 MiB
Swap total: 1431 MiB

**MOTHERBOARD**
Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
PCI bridge(s): Intel Corporation 82801 PCI Bridge (rev 81)
ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])

Any help would be great -- it may just be the heatsink overheating but we're not sure and would like some suggestions on what we should do next. Thanks!

---

### Post by charliechip95 on 2010-06-14
Any suggestions? :p

---

### Post by -humanaut- on 2010-06-14
I had a somewhat similar problem that manifested over time with a stick of ram that turned out to be incompatible with my motherboard (Really cheap Rendition ram) check the ram and make sure its all uniform

---

### Post by charliechip95 on 2010-06-14
I'm not sure why one of our ram sticks would be incompatible with the motherboard -- we've used this computer for a long time without problems until recently. Is it possible the ram went bad or something? Would the heatsink be the source of the problem you think? It's really loose -- you can swing it open like a door and look at the chip inside.

---

### Post by b0b138 on 2010-06-15
Yes, ram could go bad...it happens.  Boot to live cd and you can run a memory test. Also, assuming you have more than one stick of ram (im guessing you have 2 256meg sticks), take one out and run the computer and see if it crashes. then run it with the other one. if it still crashes with either stick one at a time its unlikely the ram.

As far as the heatsink is concerned, could be causing an overheating problem. Especially if its the one on the processor, p4s get HOT.  Heatsinks cant do their job if its not securely attached to the chip to transfer heat.  Use canned air and blow out all the dust, dust holds in heat like insulation

so after looking at the video, I'm really wondering if its a heat issue from the loose heatsink that may be on the onboard video chip (because of all the flashing lines).

---

### Post by clhsharky on 2010-06-15
charliechip95

All that info and not one mention of GPU.
Could it be Intel and what chip?

Sharky

---

### Post by proggy on 2010-06-15
this won`t help i know but that video with all that movement almost made me sick to my stomach

---

### Post by john newbuntu on 2010-06-15
Just to add to what b0b138 has said, normally when you remove the heatsink first, you are supposed to clean the original (black) thermal material before you put it back.  Then apply some thermal compound and fit the heatsink snugly.  Also make sure your cpu fan is in good shape.

---

### Post by charliechip95 on 2010-06-15
b0b138 - Okay, I just got finished using canned air inside the computer; there was a LOT of dust inside. I tried to get a good ammount out of the fans and etc. So I think maybe the computer works a little cooler/smoothly now, but it still crashes.

I'm not sure how to run a memory test. I've never done it before and I'm not sure what to burn to the disk to do it. But I did try taking out a each RAM stick and seeing how they work individually (and they are 2 256meg stacks actually :p), and the computer crashed with both tests. So I doubt it's the RAM that's the problem.

After getting some dust out of the heatsink area, I was able to give it a better look. It looks to me like the chip that was being covered (not sure what the chip is still, I'll include a video) got so hot that the area of the motherboard around it are a bit fried. The bottom of the heatsink goes along with this theory -- the materials on it are fried in the shape of the chip. Also, the heatsink is hanging lose because two of the pins on one side got lost somehow. So, there's probably a problem with this chip -- It's probably not working anymore, it got so hot. I just hope we can replace it and the heatsink without getting an entirely new motherboard. Might just need to get a new computer for that money then. :/

clhsharky - I believe this is the specs you wanted:

**GPU**
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Video of Heatsink:
[http://www.youtube.com/watch?v=2jjW8fks_b8](http://www.youtube.com/watch?v=2jjW8fks_b8)

---

### Post by wilee-nilee on 2010-06-15
A ubuntu live cd the memory check is on the same screen at the beginning just boot it and hold down a key to get to the screen.

---

### Post by charliechip95 on 2010-06-16
I ran the memory test (with 10 passes) and it came back without any errors of any sort. What's the next step? :popcorn:

---

### Post by b0b138 on 2010-06-16
hmmm...welll.... that looks like the video chip and it looks pretty cooked. Which is bad cause it can't just be popped out and replaced.  If you can take another video starting back farther so the whole motherboard can be seen then come in on that chip.

---

### Post by charliechip95 on 2010-06-16
I tried to show off more of the entire motherboard this time. Here's the new video:

[http://www.youtube.com/watch?v=Yowq934Hg5Y](http://www.youtube.com/watch?v=Yowq934Hg5Y)

If I need to replace the whole motherboard (which is what it looks like), I don't know how to find a motherboard to buy that is compatible with our computer. I've never worked a lot with hardware, so it would be a learning experience, that's for sure.

EDIT: I think this is either our motherboard or an extremely similar on: [http://www.buy.com/prod/intel-d845grgl-intel-845g-socket-478-matx-motherboard-w-video-audio-lan/q/listingid/81719881/loc/101/215095477.html](http://www.buy.com/prod/intel-d845grgl-intel-845g-socket-478-matx-motherboard-w-video-audio-lan/q/listingid/81719881/loc/101/215095477.html)
It would be nice if we could get a better, newer motherboard than this one, if we could. I'm not sure how to tell which motherboards would work with ours though.

---

### Post by b0b138 on 2010-06-16
Definitely the video chip.  But, it may be salvageable since it still kinda works, probably just getting too hot.  So.... I'd first suggest cleaning off the old hard thermal grease and applying new and reattaching the heat sink correctly. I cant tell exactly how it attaches, but one side is still attached to the mobo so I'd assume the other would be the same.  Cleaning off the heat sink will be easier if you pull it out.  Use a razor blade, rubbing alcohol and a rag. Will be a little tricky if that is a felt barrier/cushion on the heat sink.

---

### Post by charliechip95 on 2010-06-16
There seem to be to pins on the side that is attached, and the other side is missing two pins. If I use one pin on each side, I might be able to re-attach it. One newbie question: where is the hard thermal grease and where should I apply the new grease?

---

### Post by b0b138 on 2010-06-16
In a nutshell, clean off old goop so new goop has good contact with heatsink and chip

---

### Post by charliechip95 on 2010-06-16
Awesome! I'll do that soon. :)  I'll keep you updated. Just got to get some thermal grease first.

---

### Post by amauk on 2010-06-16
Random, unpredictable crashes are almost always one of two things
overheating, or a bad power supply (random voltage spikes and dips)

---

### Post by charliechip95 on 2010-06-17
I took off the heatsink today, but I'm not sure how to re-attach it properly. The metal sticking out from the heatsink isn't low enough to attach to the clips, which is pretty odd.

Also, I only have 2/4 clips, so I'd have to put the two I have apart from eachother diagonally in order to get the heatsink attached. When I tried to take one of the chips out, it didn't seem like it wanted to come out. Are they attached to the motherboard and not supposed to be removed?

Video of it: [http://www.youtube.com/watch?v=0wonJGIquDY](http://www.youtube.com/watch?v=0wonJGIquDY)

---

### Post by b0b138 on 2010-06-18
No I doubt they are supposed to be able to be removed, and you would need corner to corner to make an attempt of it working. 

They clips would push down under tension which is normal. That keeps it nice and snug against the chip.

Ok this is gonna sound crazy, but its what I would do while trying to drop as little money as possible at it. I would use string/dental floss....something non-metallic and tie down the side missing the clips to the mobo through the holes for the clips. :) Yes, this would involve taking the mobo completely out.

Well actually first, find out if its just overheating...or burnt and ruined.  Get some thermal grease, leave the computer on its side and just set the heatsink in its right place. Maybe set a can of soda on it to keep it pressed firm (UN-opened ;)) If it stays running then go with the stitches 


Or.... buy a pci (NOT pci-e) video card. They might be a little hard to find, but should only be 20-30 bucks. Then you can just go into the bios and disable the onboard video and not worry about the heatsink.

---

### Post by charliechip95 on 2010-06-18
Sounds good to me. :) So if reattaching the heatsink doesn't fix the problem, I can just get a pci video card and enable it in BIOS? I'd need a pci card with Ubuntu support though. Should most work with Ubuntu...? Would a 64-bit pci card work with our computer? Sorry for all the questions lol! :p

---

### Post by b0b138 on 2010-06-18
nvidia is supported the best. Go with a gforce 5xxx series. check ebay too, might grab one for less than 20.

---

### Post by charliechip95 on 2010-06-18
Maybe we should skip trying to fix the heatsink and just get a PCI card. It seems a lot simpler, and the GPU we have isn't that great anyway. I've noticed some odd things happen on the computer, like maybe the GPU is a little bit damaged already. :p

Looking at [http://www.amazon.com/PNY-GeForce-S-Video-Graphics-VCGFX522PEB/dp/B001E42QGM](http://www.amazon.com/PNY-GeForce-S-Video-Graphics-VCGFX522PEB/dp/B001E42QGM)
What to you think of this one? Should we go for it?

---

### Post by b0b138 on 2010-06-19
yup...much simpler :) and yup, that one would work just fine.  way better than onboard intel video.

And as a disclaimer, there is a chance (and this is just to warn you, not scare you) that the overheating maybe damaged something on the mobo. And putting in a card might not help anything if the mobo is damaged. Just a warning. it doesn't seem you have a problem till the computer runs for a bit, thus getting some heat generated. so a new vid card should fix things.

---

### Post by charliechip95 on 2010-06-19
Okay, cool. :D This guy seemed to have some problems installing the drivers though.

[http://swiss.ubuntuforums.org/showthread.php?p=6247830](http://swiss.ubuntuforums.org/showthread.php?p=6247830)

Are you sure I could get the drivers installed correctly -- how would I do it?

---

### Post by b0b138 on 2010-06-19
ok try to find a geforce 6xxx series pci card.  the driver in the repos suppports 6 and higher

---

### Post by coldraven on 2010-06-19
Yesterday I installed 10.04 on my neighbours PC and am getting exactly the same fault.
It had been running 8.04 with no problem except that it refused to update Adobe Flash.
I've done some searching and think that it is an Intel video problem, he has the 82845G chipset.

See here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

or here: [http://ohioloco.ubuntuforums.org/showthread.php?t=1448684&page=3](http://ohioloco.ubuntuforums.org/showthread.php?t=1448684&page=3)

Good luck

---

### Post by charliechip95 on 2010-06-19
Thanks for all the help!

Looking at this one now: [http://www.amazon.com/PNY-VCG62256AEB-GeForce-64-bit-Graphics/dp/B001E40O98](http://www.amazon.com/PNY-VCG62256AEB-GeForce-64-bit-Graphics/dp/B001E40O98)

There are still some people having trouble though: [http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=geforce+6200+ubuntu](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=geforce+6200+ubuntu)

I'd like to be sure it'll work before I buy it and what I would do to install the drivers. I've never tried to install PCI video cards on Ubuntu before (obviously! :p) so I'd like to know what the process of installing it (driver-wise, installing the hardware looks easy) would be.

---

### Post by b0b138 on 2010-06-19
nope, thats an AGP card not pci.

[http://www.amazon.com/BFG-BFGE84512GSP-NVIDIA-GeForce-Graphics/dp/B001LKSFNW/ref=sr_1_7?ie=UTF8&s=electronics&qid=1276990641&sr=1-7](http://www.amazon.com/BFG-BFGE84512GSP-NVIDIA-GeForce-Graphics/dp/B001LKSFNW/ref=sr_1_7?ie=UTF8&s=electronics&qid=1276990641&sr=1-7)

Up under system->administration->hardware drivers  enable the nvidia driver

---

### Post by charliechip95 on 2010-06-23
Do you think that video card, being 64-bit, would be compatible with our motherboard?

---

### Post by b0b138 on 2010-06-24
yes....that doesn't matter.  The newest geforce card is 384-bit

---

