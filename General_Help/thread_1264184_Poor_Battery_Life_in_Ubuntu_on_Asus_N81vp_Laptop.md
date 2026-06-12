---
title: "Poor Battery Life in Ubuntu on Asus N81vp Laptop"
date: 2009-09-11
forum: General Help
---

### Post by linux4life88 on 2009-09-11
I've got a new laptop, Asus N81vp-C1, and I was wanting to install Ubuntu on it but I have a problem battery life. Under Vista I get 2:45 to 3:30 of batter life but under Ubuntu I get 45 minutes to 1:15. How could this be possible? How could the battery life under Vista be so much better?

Here are the specs to my laptop:

Intel Core 2 Duo T9550 2.66ghz
4gb DDR2 800 Ram
320gb 7200rpm Hard Drive
1gb ATI Radeon HD4650 Dedicated Graphics Card
6-Cell Lithium Ion Battery

I remember on my previous laptop running XP my battery life was 2:15 but when I switched to Ubuntu it jumped to 2:30. That is why that I'm stunned that under Vista on my new laptop I get 2:45 to 3:30 of battery life but under Ubuntu I only get a measly 45 minutes to 1:15. It seems to me that the battery life should be able to at least match what it was under Vista. Any help at all would be much appreciated because since my old laptop has died I've been Ubuntu deprived and I can't wait to find a solution so I can get rid of the bloatware on my laptop, aka Windows.

---

### Post by Sin@Sin-Sacrifice on 2009-09-11
What kind of eye candy are you using? Base install wouldn't use much but once you get those apps, widgets, modules and what-have-yous running they will eat up the battery. Did you overclock? Are your fans set at full blast? You have to find out where the energy is going... when you say you're getting 2.5 hours from Vista is that idle or doing something intensive like playing WOW at full throttle?

---

### Post by misfitpierce on 2009-09-11
Can also try putting cpu on Powersave with the cpu-freq applet in bar... cuts cpu speed in half reducing alot of power and heat output saving battery life and keeping laptop cooler... Can try it out and see how it works. See if that gets you any boost? Also I see it says your using 8.10? Maybe try out Jaunty 9.04 release and see if that improves anything. Just some ideas.

---

### Post by linux4life88 on 2009-09-11
This was the battery life straight from the base install of 9.04. I added nothing to it. I've never cpu-freq applet, but I will definitely have to give that a try, thanks so much for the help.

---

### Post by shae on 2009-09-12
Your video card may support power scaleing in Windows and is not doing that in Linux.  Check with your ATI drivers.

---

### Post by linux4life88 on 2009-09-17
Okay, so I now have Ubuntu 9.04 installed. When first installed it says that I will get 45 minutes of battery life. When the proprietary ATI drivers were installed and cupfreq installed, I can now get 1 hour 30 minutest of batter life or double what I originally got. Still a far cry from 3 hours but still much better than before. Once again thanks for the help.

---

### Post by danwood76 on 2009-09-17
I would deffinatly say your graphics card is the cause, its a very powerful card.
Also do you notice your CPU dropping down its speed to the lowest rate on the gnome panel?

---

### Post by cptrohn on 2009-09-17
I use kubuntu 9.04 on my laptop because it has better powersave options for battery life.... with my laptop running kubuntu 9.04 I can change the battery setting to extreme powersave and can get about 2.5 hours on a compaq A900 with a 17in screen with WiFi connected and web browsing in that mode.

---

### Post by linux4life88 on 2009-09-17
I have installed the ATI proprietary drivers and have the card tuned down in Catalyst as far as it will go. I'm starting to think that Gnome doesn't calculate your battery life correctly. Also, I'm running the CPU on ondemand which runs it most of the time at 800 megahertz Once again thanks for the help.

---

### Post by starfly on 2009-09-17
defenetly it doesnt...

At start my batterylife on Toshiba is given to 2h 30min... but it always holds on to 3h.. !

---

