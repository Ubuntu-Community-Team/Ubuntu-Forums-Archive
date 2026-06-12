---
title: "Laptop with extra Samsung monitor trouble"
date: 2010-12-26
forum: General Help
---

### Post by Orion8 on 2010-12-26
Hi all,

I was given a Samsung SMB 2330 (TFT) monitor for Christmas.  It is pretty nice and nice and big.  Here is the problem: when I connect it to my laptop (Dell XPS M1530 with nVidia GeForce 8600M) I can use the Nvidia Settings Manager to view and use both screens, but on the Samsung screen there are lighter colored blurry lines that race up and down.  You don't see this so much on lighter windows, but any darker color shows them clearly. This is a constant whether I set the refresh rate on "auto" or 60 kH (which is what the manufacturer says it should be).

I can't for the life of me figure out how to get rid of this problem. I am fair to middling on my Linux experience, but this is the first time I have wrestled with dual monitors and I'd really appreciate any pointers  The screen is great, but the flicker is distracting to say the least.

Thanks you in advance.

---

### Post by dcstar on 2010-12-28
> **Orion8 said:**
> Hi all,

I was given a Samsung SMB 2330 (TFT) monitor for Christmas.  It is pretty nice and nice and big.  Here is the problem: when I connect it to my laptop (Dell XPS M1530 with nVidia GeForce 8600M) I can use the Nvidia Settings Manager to view and use both screens, but **on the Samsung screen there are lighter colored blurry lines that race up and down**.  You don't see this so much on lighter windows, but any darker color shows them clearly. This is a constant whether I set the refresh rate on "auto" or 60 kH (which is what the manufacturer says it should be).
.........

Test the monitor on another machine, it may be faulty or the cable is picking up interference from somewhere.

---

### Post by Orion8 on 2010-12-29
The monitor works fine using my mother's Vista machine.  I've tried other outlets in the house too to no avail.  I can't seem to find any web pages detailing problems involving 64 bit Linuxes, Nvidia, or Samsung so I have no idea...  

Any other ideas out there?  Thanks!

---

### Post by tomio on 2010-12-31
Hello,

I am having the same problem with a Samsung QX410. I didn't install the nvidia (GF 310M) drivers because they don't work. The monitor works with a HP laptop with ubuntu 10.10 and the Samsung works in Windows 7. Any ideas?

---

### Post by Orion8 on 2011-01-02
Sorry, tomio, I don't have any ideas...  The nvidia drivers work for me -- this is my first time in two years having any trouble at all.

I begin to think maybe something is wrong with my video card. I borrowed an HP screen of some sort with native resolution 1400x900 and I get the same rippling motion as on the big Samsung, just smaller (and thus a bit less noticeable).  The only other thing I can think to try is to loan the screen to an ubuntu buddy down the street and see if he has trouble with this screen.

---

### Post by tomio on 2011-01-08
After a bit of research I found that there is a VGA bug. I changed for a HDMI connection and it works perfectly.

---

