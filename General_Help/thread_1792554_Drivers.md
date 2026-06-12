---
title: "Drivers"
date: 2011-06-28
forum: General Help
---

### Post by soumyabratapaul on 2011-06-28
Actually, I am quite new to Linux(you can understand by my question), but I have used live cd's in various places. I have an Intel system, with the specifications as follows:

Processor : Intel Core 2 Duo E8400 @ 3.00 Ghz
Motherboard : Intel DG33FB
RAM : 2 * 2 GB DDR2 @ 800 Mhz

So, if I want to install Ubuntu 11.04 in my system, after the installation do I have to actually, install any drivers, like my motherboard drivers, or ubuntu will automatically supply via its internal drivers.

---

### Post by ExileAmongYou on 2011-06-28
The main things you would need to install additional drivers for are wireless and graphics cards (although if you have an integrated Intel graphics card, you might not even need them). Everything else will work automatically out of the box. After installing, you open the "Additional Drivers" dialog to install drivers that don't get installed automatically.

---

### Post by hawthornso23 on 2011-06-28
It should all just work. In particular if the live CD works OK then you should have no problems. The best thing to do is try it and see.

There are free drivers for most hardware included. You really don't have to worry about drivers or go hunting for them and download them from a website or anything like that. It all should just work. Once you get up and running there is a hardware driver tool which will automatically download and install proprietary drivers for you if you want. You just have to click a checkbox.  For most hardware there is no point, but for things like graphics cards the proprietary drivers sometimes still offer performance advantages, although the free drivers are rapidly catching up.

---

### Post by soumyabratapaul on 2011-06-28
Meaning, that supposing that I do not have any additional components that require me to install, additional drivers, I just do a clean installation of the OS, and do not even install any drivers like motherboard drivers?

But in Windows, we had to install, individual drivers for the motherboard, like Intel GMA, Sound, LAN. But in Linux, I do not have to manually do anything as such, just do a clean installation, and the rest will be taken care of?

---

### Post by mcduck on 2011-06-28
> **soumyabratapaul said:**
> Meaning, that supposing that I do not have any additional components that require me to install, additional drivers, I just do a clean installation of the OS, and do not even install any drivers like motherboard drivers?

But in Windows, we had to install, individual drivers for the motherboard, like Intel GMA, Sound, LAN. But in Linux, I do not have to manually do anything as such, just do a clean installation, and the rest will be taken care of?

Yes, most of the drivers are included directly in the Linux kernel itself. If you have any luck you shouldn't need to install a single driver yourself.

As the drivers are open-source (and often developed by Linux community, not by the device manufacturers) the drivers can be included with the operating system. There are some expectation, for example the drivers for later models of AMD & nVidia graphics cards are proprietary and therefore you must install them yourself (Ubuntu does provide a tool that will handle that for you after the install, and open-source driver is included by default altough it might not have all the features the proprietary drivers have).

Things are a bit difference on Linux side of the fence, Linux distribution developers usually take at least some responsibility of the drivers and software instead of only providing the core OS and leaving everything else to the user's responsibility.

---

### Post by soumyabratapaul on 2011-06-28
So actually, I have to only do a clean installation of Ubuntu on my system, and I will not have to worry for anything else, everything else will be taken care of.

---

### Post by mastablasta on 2011-06-28
and with that since they are opensource and not always developed by manufacturers there is bigger chance that some "exotic" hardware simply won't work. motherboard won't go to hibernation, audio wont' work etc. some of these issues are solved by installing newer opensource driver version, while some may stay unresolved or can be fixed later with kernel patches. however if computer is not latest and greatest there is 90% chance that it will all work.
 
if live CD works - install should work too. live CD is great way to test out the system.

---

### Post by soumyabratapaul on 2011-06-28
Thanks, and live cd works perfectly fine, like playing games, listing to music, watching videos, and surfing the internet too. So I think my system will also not give any problems.

Waiting for all yours' advice before installing.

---

### Post by jerome1232 on 2011-06-28
> **soumyabratapaul said:**
> Thanks, and live cd works perfectly fine, like playing games, listing to music, watching videos, and surfing the internet too. So I think my system will also not give any problems.

Waiting for all yours' advice before installing.

Are you setting up a dual boot or is this computer going to be Ubuntu only?

If it is a dual boot, it's always a good idea to make a backup of your data since you or the installer will be mucking around with your partitions. That why in the event of an accident (oops that was the wrong partition I selected, or power gets knocked out while the installer is repartitioning your disk) you don't lose all of your irreplaceable data, like pictures for the past 15 years.

It's actually a good idea to ALWAYS have an up-to-date backup around.

---

### Post by soumyabratapaul on 2011-06-28
Yeah, I am going to dual boot, and I always keep back up of all my important data. Infact I have a dual boot computer, and now I will multiboot my system. And I have an UPS, so will always, keep my system powered incase of a power failure.

Thanks to all of you for your help.

---

