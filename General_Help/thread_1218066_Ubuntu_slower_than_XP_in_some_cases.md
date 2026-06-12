---
title: "Ubuntu slower than XP in some cases?"
date: 2009-07-20
forum: General Help
---

### Post by MikeSD on 2009-07-20
Hi,
I'm relatively new Ubuntu user, but I was wondering am I the only experiencing this...

I have Jaunty 64bit on X80N Asus laptop GeForce 7000M video, 2 Gig RAM.
Nvidia drivers installed. I even have installed freshest version 185 from Nvidia site.
Visual effects are Off, all services not needed on laptop like rsync etc are Off...
And Firefox is still reacting slower than in WinXP I had on this machine before.
Tried both Firefox 3 and 3.5 shiretoko - same thing...

I also have pretty antique Averatec 1000 laptop with 512 RAM and some simple Intel videocard. And on THAT laptop Jaunty is running same speed as XP.

I'm really curious why I feel its running slower on relatively new laptop with good enough hardware? Bad support for Nvidia chipsets or something?
I have no idea, thought someone could suggest...

---

### Post by jerrrys on 2009-07-20
Im guessing thats Jaunty 32bit on that old lappy...

---

### Post by benj1 on 2009-07-20
firefox has been written and compiled with windows in mind thats why it tends to be faster, ive even heard reports that firefox running in wine is faster than firefox for linux  [here]("http://ubuntuforums.org/archive/index.php/t-569840.html")

things like crappy flash support don't help either

---

### Post by MikeSD on 2009-07-20
> **jerrrys said:**
> Im guessing thats Jaunty 32bit on that old lappy...

Yes.  Do you mean that 32bit Jaunty would be faster even on laptop with 64bit CPU ?
I have tried running both from live CD - I didnt notice much difference, but in some forums I've read that 64bit version is faster on 64bit CPU's, so I installed 64bit.


> firefox has been written and compiled with windows in mind thats why it tends to be faster, ive even heard reports that firefox running in wine is faster than firefox for linux here
things like crappy flash support don't help either

Yes, probably problem is with firefox, but that's browser I'm using and most used application of all for me... Flash is really not as fast as on WinXP, I've installed Adobe's player, others seems to be even worse.

I dont know, it seems me that just on some types of hardware Ubuntu performing worse... I also been trying it (64bit Jaunty) on MSI PR211 laptop with 2 Gigs RAM - it's running very very smoothly... And X80N Asus laptop has about a same config, just Nvidia instead ATI, and it's slow on it...

---

### Post by MikeSD on 2009-07-26
Maybe those who experience slowness in Ubuntu compared to WinXP will find this thread helpful... 
I finally found a solution to make it run fast on machine where it seemed me been slower than WinXp...

I had to change GNOME to Xfce and now its all fine :)

Couple hours of setting up appearance, keyboard layout switch and other stuff in Xfce and I finally got Ubuntu and Firefox in it running really fast on this my laptop :)

---

