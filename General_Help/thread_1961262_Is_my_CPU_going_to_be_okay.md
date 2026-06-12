---
title: "Is my CPU going to be okay?"
date: 2012-04-18
forum: General Help
---

### Post by MutantJohn on 2012-04-18
Hello Everybody,

I have an AMD Phenom II X4 955 Black Edition processor and I was playing Battlefield Bad Company 2 through Wine 1.5.1 and I saw my CPU temp spike to 70C when the max safe operating temperature is 64C. 

I wasn't playing all that long and everything seems to working fine but have I done any damage to my processor? 

Also, I'm not worried about a bad heatsink or anything like that because my temperatures never ever go that high except for just this one instance. 

I don't have overclocking enabled on my computer so I'm curious why it would allow itself to go up to 70C even though it's not supposed to. Also, the fan speeds on my CPU while playing were kinda low as well. Is it just a fan speed wine error?

---

### Post by Shazaam on 2012-04-19
Do you have C&Q enabled in your pc's bios?. Might want turn turn it off while gaming.
70c is bad only if you let it run like that for a while. If it temporarily spiked to that I don't think you did any harm.

---

### Post by Mark Phelps on 2012-04-19
I have an AMD Phenom II 4-core and I have to work hard to get it up into the 40's -- usually it's down in the upper 20's or lower 30's.

You should check your BIOS settings to ensure you have temperature alarms set -- I don't think they are by default.

---

### Post by Bobhuber on 2012-04-19
What motherboard are you using ? I've had that happen using a quad core on a dell board and it would only do it during backup (fsarchiver). Make sure your Bios is up to date and I would NOT turn off cool and quiet.

---

### Post by QIII on 2012-04-19
I have the same CPU running 100% 24x7x365 (except for maintenance and new kernel updates).  Adding 10 degrees to the infamously low reading from the on-die thermistor and K10temp, I stay around 36 - 38, but with an aftermarket HSF.

I would be unhappy with a Phenom II that reached 50 and would shut it down approaching 60.

I'd be considering funeral arrangements at 70 for more than a very few seconds.

You need to reconsider your cooling arrangement.

What might have changed?  Thermal compound breaks down and dries over time.  All it takes then is a bump to the case to jar the HSF enough for the contact to be broken.  That's just one of many possible scenarios.

---

### Post by 2F4U on 2012-04-19
The problem might be the graphics card. It blows hot air inside the case and the case fans may not be able to get it out of the case. This would then also increase the temperature of the CPU.

---

### Post by QIII on 2012-04-19
Depends on the card, somewhat.  Although nothing is perfect, I use cards that exhaust out the rear of the case for just that reason.

I do a lot of GPGPU work and I have one machine with 4 5870s that exhaust out the rear.  It's loud as hell when it cranks because the top three cards get limited access to air and the fans have to really work hard but the case temperature is not affected to the point that I get anywhere near critical values on my CPU temp. 

But it is certainly true that some cooling arrangements, like cards that exhaust to the side or front, can make the cast pretty hot inside.  Some can even blow hot air right on to disks.  Particularly the dual GPU cards with fans in the center.

---

### Post by MutantJohn on 2012-04-20
> **Shazaam said:**
> Do you have C&Q enabled in your pc's bios?. Might want turn turn it off while gaming.
70c is bad only if you let it run like that for a while. If it temporarily spiked to that I don't think you did any harm.

I like this guy the best. So, there's been no damage permanently to my CPU it seems as it performs just as fine as ever. 

He's right, however about the C&Q because I do have it enabled and I noticed that my fan speeds were about 1200 RPM short of where they should've been so upping the fan would do it fine.

I use the stock heatsink and I'm just amazed that I could take this chip that high and not have it break on me. I say, congratulations, AMD.

---

### Post by for.i.am.root on 2012-04-20
That's if your temps are being read properly.... My rig is off by about 12 degrees.

---

### Post by Mark Phelps on 2012-04-21
I would still be concerned about the heat.

I did a test of my 6-core AMD and ran it for an hour with all six cores at nearly 100% -- and the temp reported never got above 43C. I used a video conversion app that utilizes all the cores.

And yeah, I know that could be reporting low -- but it's still a lot different from the temps you're reporting.

---

### Post by MonkeyPaw on 2012-04-21
Graphics cards routinely hit 70C under load, but CPUs are not designed for it.  Are you sure you weren't getting the readings for the CPU mixed up with the GPU?
 
If the reading is true, then I'm thinking you have an issue with your cooling. Either the heatsink is undersized, not mounted correctly, the fan has failed, or the whole assembly might be clogged with dust. Regardless, the BIOS can be set to alert and/or shut down at a thermal threshold. This should work independently of the OS you run.

As far as if your CPU is okay. I'm sure it's fine. The thermal threshold is likely spec'ed lower than the real point of failure. You might have more trouble if this was a continuous load temp, if for no other reason than because it stresses the surrounding components that must supply power under high heat (more resistance). Open the case and observe the system in action. My Phenom II X4 never seems to get hot, much less 70C.

---

### Post by pqwoerituytrueiwoq on 2012-04-21
are you over clocking it? some boards have a auto over-clock feature make sure the clock and voltage is set correctly
i have a AMD 965 phenom II x4 with the stock heatsync and fan it stays pretty cool at it stock 3.4Ghz
does your case have a said e airduct or fan? if not yuo may want to consider making one there you just need a 8 CM hole saw, duct tape (put it over the area you are going ot use the saw), a 80mm dust filter, and a 80mm fan alternativly yuo can use a grill and a air duct 
u used a grill and home made duct on my 965 and it was staying in the 40s to lower 30s iirc

---

### Post by MutantJohn on 2012-04-22
Actually, I got into undervolting and it seems to be working fine when under load but my idle temps are higher. And by working fine, my under load temps are now much, much cooler than before.

I have AMD Phenom II x4 955 BE if I didn't mention it earlier.

---

### Post by MutantJohn on 2012-04-22
And my computer is over a year old and has been checked out before by Geeksquad so I think if anything was glaringly obvious they'd have caught it and my computer wouldn't be over a year old.

This was honestly just a one time thing.

---

### Post by NadirPoint on 2012-04-22
I hope AMD has similar built-in protections to my several years old 2.4Ghz Intel Quad Core CPU that self-invoked thermal shutdown probably a dozen or more times due to an improperly installed fan.

It's been fine for a couple years now since getting that fixed.

---

### Post by MutantJohn on 2012-04-22
Alright, so I finally fixed everything.

Playing Heroes of Newerth with everything maxed and whatnot: 48C Max. Before, it was around 59C Max. This is dropping from 1.33 V to 1.17 V.

Also, playing Trine on max through Desura drops my CPU from a max of 61C to about 53C.

Also, when I was changing voltages, somehow my cpufreq settings were messed up so my ondemand governor was set from a low frequency of 3.2 Ghz to 3.2 Ghz so I fixed to from .8 Ghz to 3.2 Ghz and now everything is running absolutely perfectly and I won't have to worry about killing my processor anymore.

And my CPU fan is a lot happier too, ha ha.

---

