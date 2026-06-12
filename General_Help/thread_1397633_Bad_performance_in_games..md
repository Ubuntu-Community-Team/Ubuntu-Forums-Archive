---
title: "Bad performance in games."
date: 2010-02-03
forum: General Help
---

### Post by Marquezzz on 2010-02-03
First off, hello everyone. This is my first post.

So im running Ubuntu 9.10 on an HP Pavilion 520n.
Specs:
RAM: 512mb
HDD: 60gb
GFX: Onboard Intel (Not sure what the specifics are)

My problem is that most games I try to play are laggy, even MS-DOS games (ran through DOSBOX .73). The only DOS game i could get working without lag is Eye of the Beholder, anything beyond that is pretty laggy, playable, but to much to enjoy. I have the same problem with games through Wine. Simcity 2000, Starcraft and Total Annihilation. The ones through Wine are unplayable because of lag. Any ideas on how I can fix this, and if I need to clarify something just ask.

Thanks in advance.

---

### Post by t4thfavor on 2010-02-03
I believe the Intel (R) 810e can only have between 1 and 8 MB of video memory, I am sorry, as it seems your video card is the limiting factor. 

you may check your BIOS, and see if there is an option to increase the amount of RAM you share with the system RAM. As a general rule, intel graphics do not perform as well as ATI/NVidia.

---

### Post by diablo69er on 2010-02-03
Games are laggy...well with 512 mb..why wouldn't they be?  Even on my windows machine 4 gigs of ram and a nice video card still causes games to lag.  I'd update your hardware if your really serious about gaming, or just buy a ps3 and be happy :)

---

### Post by Marquezzz on 2010-02-03
Thanks for the reply.

even with 8mb of vram these are MSDOS games. My mind just can't handle that this computer, which is so much more advanced than a computer with a 300mhz processor and 6mb ram can't run a DOS game at a decent speed. Also, a while back I had this same computer setup with Ubuntu 9.06. Wine ran Nancy Drew Secret Mansion (or something like that) better than it ran in Windows. Im gonna see if Nancy Drew works just as well in wine as it did in 9.06... if I can find that CD.

---

### Post by t4thfavor on 2010-02-03
I am talking video memory, there is far too little on the integrated intel card he is using. It's perfectly normal to run linux games on less than 1GB so 512 is not out of the question if you have a good Video card.


Your forgetting the emulation layer, and the host OS in the calculation above. Load up dos 6.22 on that pig, and you won't be able to play them either, they will run toooo fassstttt!!!!

Also make sure compiz is off by selecting System -> Prefs -> Appearance, and then setting Desktop Effects to None.

---

### Post by KillerKellerjr on 2010-02-03
I would just go buy a cheap Nvidia PCI graphics card off ebay for $15-$30 and that will probably solve your issue.  You could also dualboot Windows XP since you can pickup keys for $5 off craigslist these days.  They will probably run better in the windows environment, I am not sure if your system would handle virtual machine to run XP virtually in Ubuntu...anyone else?

---

