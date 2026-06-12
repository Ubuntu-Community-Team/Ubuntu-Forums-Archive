---
title: "Asus 1215B or HP dm1z running Ubuntu?"
date: 2011-07-16
forum: General Help
---

### Post by JavaNut13 on 2011-07-16
Hi all,

I am looking to upgrade my netbook (Acer Aspire One 532h) slightly. I have a budget of NZ$750 and have found the two main contenders: the HP dm1z and Asus 1215B. Both have an AMD E350 dual-core 1.6ghz processor and 1366X768px resolution.

After looking about on the internets, the dm1z seems to be a pain to put Ubuntu on, but the 1215B has less problems (only minor issues - sleep, volume, compared to trackpad and WIFI)

USB 3 is not a real selling point to me. I was leaning towards the HP because it is thinner (1.2" tapered to 0.8" vs 1.5" to 0.9") and generally nicer look & feel. Also keyboard looks nice.

They are priced as follows:
HP dm1z - NZ$668 (3gb RAM, 320gb HDD 7200rpm)
Asus 1215B - NZ$713 (2gb RAM, 500gb HDD 5400rpm)

Basically, what do you think? is the extra (lots..) difficulty worth it.. or go for the similar Asus and have less trouble?

Cheers,

Will.

---

### Post by Wahlgren on 2011-07-21
I got the Asus 1215B and like the design of it and screen size. But, there are some things to have in mind. It looks like allot of people, including myself, was unlucky to get a defected touchpad that makes 1215b frustrating to use. There is a fix to it tho and it involves opening up the laptop and tinker with the touchpad, removing some silver tape protection or something? 

Not so fun after paying for something you expect to work good. The other issue is with the AMD Radeon proprietary driver. It seems AMD isn't doing their best to release a good driver for us Linux users, so performance isn't the best and I also noticed 1215b runs hotter on Linux than in Windows. The 5400RPM hard drive that comes with 1215B is not the fastest around and I would look for another HDD to replace if you have the economy for it. At the moment I'm looking at the Seagate Momentus XT 500 GB 2.5" Hybrid SSD Hard Drive, just have to check its compatible with Ubuntu ;)
 
Asus 1215B is good for it's price tho and because the hardware is new there is to expect problems with running Linux on it. I use Xubuntu 11.04 at the moment to try and get some extra performance boost and it works ok. Still wished I had done more research before buying this computer tho...

Good luck to make your choice and read allot of reviews out there before buying one!

---

### Post by JavaNut13 on 2011-07-24
Cheers mate, I think I will wait til 10.10 comes out - the price will  be lower and support for the e350 will be better!

---

### Post by Redblade20XX on 2011-07-25
Here's the problems that the dm1z had after a fresh install 10.10 64bit which have been resolved.

- No wifi                              Fixed: The wireless drivers are given by the manufacture although you'll have to patch them yourself but there are how to's on the internet.

- Disabled Touchpad          Fixed: There are patches by numerous people that can enable those functions which are disabled.

- Bluetooth Adapter Not Identified     Fixed: There is a patch which enables the bluetooth which was caused by the integration of wifi card and bluetooth (since wifi card didn't originally have drivers)

- Graphics Card unsupported natively  Fixed: Ati Catalyst 11.6 fixed most of the graphic problems that occurred with the open source driver (note: On 10.10)  but it is closed source and you'll have to install the driver yourself. 

I'm happy with 10.10 on the dm1z, which most of these problems were resolved for me, but the newer ubuntu versions have more bugs.

---

### Post by Vaphell on 2011-07-25
you can get drivers from PPA
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

