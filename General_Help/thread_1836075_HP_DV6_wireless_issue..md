---
title: "HP DV6 wireless issue."
date: 2011-08-30
forum: General Help
---

### Post by Icculus574 on 2011-08-30
I recently purchased a Pavilion DV6 from Best Buy after my old trusty EEE901A finally bit the dust.

Wifi works fine in Windows and Ethernet works fine in both Windows 7 and Ubuntu 11.04, but for the life of me I can't get wifi to work in Linux.

I've tried many many solutions offered on these forums in more threads than I can remember, but I've had no luck so far. I think part of the problem might be that my particular DV6 has no extended model number in the branding and Google provides no results for the detailed model number - which has made it difficult to say the least.

The wireless card is the RT5390 and I've gone through all of the instructions in other threads to install the correct driver(x64 with all the updates as well as trying to install the newer driver version with the updates rolled in) and the Additional Drivers window shows the driver alongside my ATI drivers so I believe it's installed correctly. I've also removed the other Ralink wireless driver which seemed to be pre-installed (rt2860sta) to see if that was the conflicting issue. The card shows up in iwconfig, but not in ifconfig.

My wireless light is orange (which is off) and pressing it does nothing. When I boot the computer, it defaults to orange and doesn't actually flip to white until Windows is already loading. I also have no option in my BIOS to enable/disable wifi on boot.

My product's official name is HP Pavilion dv6 Notebook PC and my product number is LW262UA#ABA.

I'm fairly well versed in day-to-day Linux stuff, but when it comes to trouble shooting and digging deeper my knowledge is a bit random and spotty. Because of that, treating me as an absolute beginner might be better. It might help those who have even less knowledge than me at a later date.

Thanks so much to everyone in advance. I've never had so much trouble running Linux on a laptop as I've had with this particular model.

---

### Post by Mark Phelps on 2011-08-30
I have an older HP laptop with much the same issue -- except that the light goes from orange (off) to blue (on).  And, I discovered that pushing the button when inside Ubuntu has no effect at all.

So, basically, if Ubuntu starts up with the button as orange, I have to boot back into Windows, press the button (to turn it on) and then boot back into Ubuntu.

---

### Post by Icculus574 on 2011-10-13
Still haven't been able to find a solution, but when talking to HP support (in which they pretty much blew me off and said that you need to be in Windows to enable Wifi), I did get the model number. I hope it helps.

HP DV6-6135dx

Thanks again.

---

### Post by Mark Phelps on 2011-10-13
Sorry, but from everything I've read, the problem is that there is no device driver installed in Ubuntu that handles the Wifi On/Off button.

There is a LONG thread here where someone else was trying to get such a driver installed by using the Broadcom firmware -- but after pages of posts, they still were unable to get that working.

Like memory card readers, these WiFi buttons appear to just NOT be supported very well in Linux distros.

As I said earlier, my only working solution was to boot into Windows to turn ON WiFi, then reboot into Ubuntu -- with it still turned on.

---

