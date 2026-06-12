---
title: "Some programs run very slow 9.10"
date: 2009-11-02
forum: General Help
---

### Post by Chryseus on 2009-11-02
Well I made the upgrade to Karmic from a clean install which went perfectly.
However a little while later I decided to play some Haven & Hearth which is a Java based multiplayer game, when I started it I found it to be running very slow including the mouse cursor which jumped all over the place, needless to say it was impossible to play.

At the time I assumed it was just some kind of bug in the game due to a recent update, I then tried to play Minecraft (another Java based game) but although that worked a good deal better I still noticed some minor freezing, in addition to that people in my server complained of severe lagg which I noticed myself.

Now at this point I thought something was up with Java so I spent a while trying to sort that, a little later I noticed that flash movies in firefox were stuttering quite badly.

So perhaps this is a network problem, but I cannot see what is the cause. Everything works fine on Windows and I'm using the exact same configuration in Ubuntu. Any suggestions you could give would be very helpful.

Also I never had this problem in 9.04 so something new must be causing it.
:(

**System Specs**

Intel Pentium 4 3.06GHz
3GB DDR2 533MHz RAM
nVidia GeForce 9600GT 512MB PCI-E (using 173 drivers from apt)
160GB HDD (100GB EXT4, 2GB SWAP, 58GB NTFS)
RealTek HD Audio
Intel 915P chipset
Emprex 22" Monitor 1680x1050@60Hz

---

### Post by !! hack-back !! on 2009-11-03
the same :(

---

### Post by dbyjazz on 2009-11-03
.

---

### Post by dbyjazz on 2009-11-03
first try re-booting. that fixes a lot of my little problems

if that doesn't work try reinstalling Java

once you have tried the two simple things report back :)

---

### Post by garvinrick4 on 2009-11-03
How many kbs are coming in thru connection?

---

### Post by Chryseus on 2009-11-03
On Windows I normally get around 100-150kb\s, however I only seem to be getting around 10-50kb\s on Ubuntu.
Also I have tried reinstalling Java, but as I said this also effects playing online flash videos.

---

### Post by P4man on 2009-11-03
why are you using the 173 drivers?
185 is the recommended.

---

### Post by Chryseus on 2009-11-03
> **P4man said:**
> why are you using the 173 drivers?
185 is the recommended.

Yeah I tried the 173 drivers to see if that was the problem but that did not help.

---

### Post by Chryseus on 2009-11-03
It seems OpenOffice and other local Java programs are not effected, so this must be some kind of network problem. What it is I have no idea, I use the exact same configuration on Windows.

---

### Post by garvinrick4 on 2009-11-03
That is sure a slow connection, that is close to dial-up speed. And 10 to 50 would
not play nothing. See why so darn slow.

---

### Post by Chryseus on 2009-11-04
I get 100-150kb\s on Windows and streaming videos play just fine.
The speed seems to be about equal now on Ubuntu, the videos streams perfectly however playback stutters a lot.

I don't think it's a network issue, it seems to be something else that's causing slow framerate on streaming videos and games.

---

### Post by garvinrick4 on 2009-11-05
HMMM stutters like not enough packets are getting through sometime's like not enough kbs
Like internet connection does not have enough bandwidth and or congestion on ISP.

This day and age most all machines have enough RAM and Processor speed. 

Do you have dial-up?   Why so slow?  Sure seems like something is to slow.

Down load bmon  program to see how fast sending and receiving.  It is a simple 
bandwidth monitor.

---

