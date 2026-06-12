---
title: "Video Card Problems"
date: 2009-09-11
forum: General Help
---

### Post by mharrison on 2009-09-11
I recently had to remove my NVidia card from my box because it kept overheating no matter what I did (cleaning and all of that) so I went to my onboard video which is a VIA Chrome9.  I was in the process of redoing my system so I am working with a clean install of 9.04.  

My problem is that I cannot enable any of the desktop effects even though Synaptic is showing me the driver package for my video card is installed.  Is there something I should do to be able to enable these settings?

Just for reference, my Motherboard is a MSI K9VGM-V.

Thanks for any help.

---

### Post by gavoby on 2009-09-11
Maybe the video card just isn't good enough.

---

### Post by mharrison on 2009-09-11
> **gavoby said:**
> Maybe the video card just isn't good enough.

I somehow doubt that being the motherboard is only a year old, works fine in Windows with the onboard video card, and all of the documentation I found when I googled for Linux support for my video card/mobo combo came up saying it should work just fine....just happens that I didn't find anything saying how to configure it to make it work just fine.

---

### Post by P4man on 2009-09-11
there are no good VIA chrome drivers for linux. VIA is not giving the specifications, openchrome is as "good" as it gets, but you're pretty much limited to simple 2D. If that works well, consider yourself lucky already. You can try of course, some ppl even get some 3D working:
[https://help.ubuntu.com/community/OpenChrome#openChrome%20and%203D](https://help.ubuntu.com/community/OpenChrome#openChrome%20and%203D)

> For desktop PC users a definitive solution is to use another graphics card. 

(or another OS)

---

### Post by khelben1979 on 2009-09-11
Have you ever wondered about changing the cooler of the card? (you'll lose the warranty of course)

---

### Post by mharrison on 2009-09-11
> **khelben1979 said:**
> Have you ever wondered about changing the cooler of the card? (you'll lose the warranty of course)

I've thought about it, but haven't gone much beyond that.  I took the fan off and cleaned out the fins and also cleaned out the entire system of dust and made sure everything else was working fine, but if I put the cover back on the case, sooner or later the machine shuts off and won't turn back on until I pull the plug and put it back in.

I thought at first I had other issues, but once I removed the Nvidia and put the cover back on, I didn't have the issue anymore.  I may just buy a new card, but the one I have is only a year old...The only good part of removing the card is that I don't get the random system alarm going off when Ubuntu first boots up and hits the PCIx error...I'm sure there is something I should do about the error, but it never stays up long enough for me to record the entire thing, and the system alarm only happens once in a while and a hard reboot before anything is mounted normally takes care of the problem....but since I only reboot my computer when an update requires it, or when I shut the machine down on extended time away from home, I never really cared much.

---

### Post by P4man on 2009-09-11
Im guessing it wasn't an overheating problem, but your powersupply being pushed over its limits..?

---

### Post by mharrison on 2009-09-11
> **P4man said:**
> Im guessing it wasn't an overheating problem, but your powersupply being pushed over its limits..?

Interesting point....I didn't think of that because it ran fine for so long with the same setup, but it might be worth a shot pulling my backup drive out and trying it again....Not sure of the differences in power usage of a hard drive vs. a video card, but it would make for a good time killer this weekend.

---

### Post by P4man on 2009-09-11
Hmm. not certain pulling a HD will help much, if at all. I think a drive pulls most power from 5v or even 12v, whereas a videocard I think from the 3.3v. If your bios has a "PC health" page, you can have a look at your PSU voltages in there with and without the nvidia card. If there is a considerable difference, an underpowered PSU is a good bet. What nvidia card was it?

---

### Post by mharrison on 2009-09-11
ZOGIS ZO84GS-EL GeForce 8400 GS


Edit:

Just was looking over the old order history when I bought the parts for this box and I can't believe I overlooked the fact it only had a 300w power supply

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167010](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167010)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103257](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103257)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814136025](http://www.newegg.com/Product/Product.aspx?Item=N82E16814136025)
Also have a 750gig SATA drive, a IDE DVD Writer and 200gig Hard Drive....again, I can fix alot, but power usage is my weak spot.  I'll take a look at the Health Status with and without the video card and see if I notice a big change....And just to note, the same problem with the shutting off happens if I use Windows as well....and it doesn't shutoff all the time...it's more like if I have the box on for 3 days, it may shut off once, but it may not....but when it does, it doesn't always come back on unless I monkey around inside a bit.

---

### Post by gordintoronto on 2009-09-11
> **mharrison said:**
> ZOGIS ZO84GS-EL GeForce 8400 GS

Edit:

Just was looking over the old order history when I bought the parts for this box and I can't believe I overlooked the fact it only had a 300w power supply


If the power supply is actually delivering 300 watts that should be more than adequate; your processor has a very low requirement.

In the pictures on newegg, there is an exhaust fan in the case.  If that fan is working, the video card shouldn't overheat.

There is an excellent program called sensors-applet which can display the temperatures of your processor, video card and hard drive.  I think it depends on lm-sensors, which is slightly tricky to install, but is well described by other posts in the forums.  My video card generally runs around 48 C, and my hard drive reports 33 C except on a hot summer day.

---

### Post by P4man on 2009-09-11
Well, an 8400 is hardly a huge power hog, id be surprised if it drew much more than 25W,  but if the PSU is flaky, I guess anything can push it over the edge.

---

### Post by mharrison on 2009-09-11
Thanks for the suggestions everyone.  I guess what I am going to have to do when I get home from work is to put it back together the way it was and setup some monitoring to keep an eye on the temps.

I'm also going to keep an eye on the PSU and see if I can determine if it is starting to go flaky on me or not.

---

### Post by mharrison on 2009-09-24
So I have the sensors-applet installed and running, and over the past week I have been watching the temps on my system, and they have always remained fairly constant.....The Hard Drive sits at around 109 F, the GPU at around 127-129 F, and the processor ranges from 64-68 F depending on what I am doing.  I checked the PSU meter in my BIOS and everything appears normal....

I even went as far as to test my memory to make sure there wasn't a bad spot and that all tested out fine.  I guess all I can do now is possibly try to get my hands on a new PSU and see if the problem goes away with it.  The hard part is I can never tell when the computer will shut off.  Just 5 minutes ago I was reading an e-book, barely using any system resources and the computer shut off.

I have cleaned everything out very well, even put new thermal grease on my processor fins/fan.  

Don't know if anyone has anything else to test, but it looks like the PSU is the only thing remaining that could be causing this, as it has done it without the GPU installed, using the onboard video.

---

### Post by gordintoronto on 2009-09-25
> **mharrison said:**
> ..and the processor ranges from 64-68 F depending on what I am doing...


It sounds like you're getting a bad reading for the processor.  There's no way it should be colder than room temperature.

On many modern systems you can get the temperature reading in the BIOS.  When you reboot, see what it says.  (LM-sensors doesn't support my CPU yet, so that is the only way I can see my CPU temperature.)

---

### Post by mharrison on 2009-09-25
> **gordintoronto said:**
> It sounds like you're getting a bad reading for the processor.  There's no way it should be colder than room temperature.

On many modern systems you can get the temperature reading in the BIOS.  When you reboot, see what it says.  (LM-sensors doesn't support my CPU yet, so that is the only way I can see my CPU temperature.)

Actually, it is sitting right around room temperature....It's turning to fall here so the weather outside can go from 58 to 70 in a matter of an hour, and I don't have the air or furnace turned on, so the house sits at the outside temp pretty much all day long.  I'll double check the BIOS reading, but the last time I checked it, it was almost right on with LM.

---

### Post by P4man on 2009-09-25
Its still impossible. i don't know what cpu you have but *any* modern desktop CPU would draw upward of 5 Watt iddle and up to 80-100W under real load, and they are usually like 10x10mm². Thats the power draw of a light bulb on the size of a pinhead and that means they are HOT and need heatsinks and almost always fans to keep them from melting. 

Unless you have a refrigerator, there is no way you could keep them below 30°C on air cooling. Not very likely even with watercooling. 65-68° CELCIUS however, that i want to believe.

Something is misreading for sure if it says 68°F.

---

### Post by gordintoronto on 2009-09-25
> **P4man said:**
> ... Thats the power draw of a light bulb on the size of a pinhead and that means they are HOT and need heatsinks and almost always fans to keep them from melting. 

Unless you have a refrigerator, there is no way you could keep them below 30°C on air cooling. Not very likely even with watercooling. 65-68° CELCIUS however, that i want to believe.

Something is misreading for sure if it says 68°F.

My CPU draws up to 80 watts on the size of a postage stamp.  The case has excellent air flow, the CPU has the stock heatsink and fan, and it typically measures in the high 40s Celsius.

---

### Post by P4man on 2009-09-26
> **gordintoronto said:**
> My CPU draws up to 80 watts on the size of a postage stamp.  The case has excellent air flow, the CPU has the stock heatsink and fan, and it typically measures in the high 40s Celsius.

The heatspreader (the aluminium plate) you see is the size of a postage stamp, but the actual chip below is even smaller. Here you see a naked die of a Penryn (Core 2 Duo ):

[http://www.tweaktown.com/news/9964/intel_penryn_cpu_die_caught_on_camera/index.html](http://www.tweaktown.com/news/9964/intel_penryn_cpu_die_caught_on_camera/index.html)

And a look-through pic (of what i think is the C2D mobile variant, with a much smaller packaging then a desktop chip):

[http://laptoping.com/wp-content/Intel_Penryn_Dual_Core.jpg](http://laptoping.com/wp-content/Intel_Penryn_Dual_Core.jpg)

Half of that cpu is cache memory and hardly draws any power. That gives a thermal density under load that dwarfs the tip of any soldering iron.

---

### Post by mharrison on 2009-10-04
So I'm going to consider this issue solved....I was doing my monthly cleaning of the machine and decided to switch the RAM sticks around and after I did that, the machine would shut off about 2 minutes after booting into Ubuntu.  I pulled the 1st stick and it hasn't shut off since....so I guess the RAM test lied and I did have a bad stick after all.

Thanks for all of the help!

------

Update:
After I wrote this, the next day to be exact, the problem came back.  After doing a bit more digging around I decided to swap power cords.  Before I did this, I could not keep the system up for more than 3 hours at a time, since I swapped cords, I have been up for 30 hours straight now without an issue.  Silly how you can work on computers for 10+ years and still get burned by the simplest of things.

---

