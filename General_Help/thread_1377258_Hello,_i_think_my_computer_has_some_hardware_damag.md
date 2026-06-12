---
title: "Hello, i think my computer has some hardware damage but im not sure whats up. Help!"
date: 2010-01-10
forum: General Help
---

### Post by sensay on 2010-01-10
Hi. This will be a pretty lengthy post but i hope someone takes the time to read!

Firstly, my machine dual boots windows (for the games) and ubuntu. I have noticed problems over both operating systems. In windows when i try and game the performance is horrible and sluggish, sometimes it will play fine for a while other times not. Its not indicative of temperature issues because the performance can sometimes start bad right off the bat or sometimes get better once it has gone bad. There have been three recent agmes that are unplayable because of this, Draconis 2 would freeze the game screen but still allow me to navigate aroiund (sounds worked, i could HEAR myself walking about), DIRT2, would play at 60FPS for a while then nosedive to about 10 and never fully recover and most recently vancouver 2010 this games does the same as dirt2 only the slowdown happens within 10 seconds ofplay and thus i cant even get past menus.

In ubuntu i get VERY frequent grey screens when i try and do more than very basic tasks. A good example would be trying to navigate firefox with transmission open, this will give me grey screens and crashes nearly 100% of the time. Applications tend to stop working as well. I have only just reinstalled ubuntu because in my last install of 9.10 i lost access to over half my apps. Some examples, firefox would not start because of a segmentation fault, VLC would open but not play and never close. (in fact, a LOT of apps can only be closed via the kill command).

Since reinstalling, the crashes and grey screens appear but FF and other apps appear OK.

Ok, so i have limited knowledge and these are the conclusions i have come to so far:

Its not overheating. I keep the machine cool and as mentioned above, the problems dont seem heat related.

I dont beleive its my HDDs, i use two drives 1 for ubuntu and 1 for win. Unless there both dying then it cant be them. Also both drives are new and appear to pass all seatools tests with ease.

I dont think its my RAM. I have recently just replaced a 1GB stick of kingston hyperX that blew in my machine so the RAM is brand new.


SPECS:

Geforce 9800GT
Asus M2NSLI Deluxe
1GB Kingston hyperx ddr2 AND 1gb cheaper ram ( i know you shouldnt mismatch but the same problems happen on just 1GB and ive had no problems like this before)
amd athlonx2 2.9Ghz
OCZ StealtheXtreme 550W PSU

PLEASE HELP GUYS!

---

### Post by wirelessmonkey on 2010-01-10
It sounds like either a graphics problem, or a memory problem.  Memory is easier to test, run memtest.

---

### Post by sensay on 2010-01-10
Sorry, should have added that i did do a memtest when i got the new stick. Both sticks checked out OK after a couple hours testing.

Thanks for the reply though, any other ideas? When you say graphics problem what do you mean? The card is still under warranty so if its faulty i would simply exchange it. Its always served me well up to now though. Also, would that explain the problems that im experiencing in ubuntu? Seeing as i ONLY use win for games it seems somewhat obvious that the only problems id notice would be of a graphical nature but the ubuntu problems are affecting other areas than my GPU.

Other things to add. Ive noticed that my extracting speed for archives has dropped a bit too.My drives (seagate 250 and 320) both extracted at about 15Mb/s and now go anywhere between 7-12MB/s. Added to that im fairly sure ive noticed slow down when copying files from one drive to the other (something i need to do fairly regularly). I dont know if this is relevant because the drives have passed long and short tests in seatools. 

Cheers.

---

### Post by stinkeye on 2010-01-10
In your sig you have another desktop.
Try out the card from the other desktop.
If the other card has problems as well, swap your power supplies and test.

---

### Post by sensay on 2010-01-10
Hi. I tried out the 8600 and test in windows on draconis 2 and still got the same frozen screen. Swapping PSUs is not an option, the PSU in the second desktop is not enough to even fully power the 8600 but as its only used for light desktop activities it performs adequately.

However, im starting to think that its a motherboard problem. Its one of the last suspects left. Im concerned that my ubuntu problems arent graphic related in the least and surely if the mobo was to blame that would explain why im getting problems all over the place? (transfer speeds, general performance, software crashing, 3d games crashing/lagging)

Now, i do have a spare motherboard, albeit a POS. But its compatible with all my current hardware. Im probably gonna put it in and see what happens but will this require a reinstallation of both windows and ubuntu? I know when you switch to different CPU architecture windows freaks out but will it matter if the architecture matches? (amd for amd)?

Cheers

---

### Post by stinkeye on 2010-01-10
> **sensay said:**
> Hi. I tried out the 8600 and test in windows on draconis 2 and still got the same frozen screen. Swapping PSUs is not an option, the PSU in the second desktop is not enough to even fully power the 8600 but as its only used for light desktop activities it performs adequately.

However, im starting to think that its a motherboard problem. Its one of the last suspects left. Im concerned that my ubuntu problems arent graphic related in the least and surely if the mobo was to blame that would explain why im getting problems all over the place? (transfer speeds, general performance, software crashing, 3d games crashing/lagging)

Now, i do have a spare motherboard, albeit a POS. But its compatible with all my current hardware. Im probably gonna put it in and see what happens but will this require a reinstallation of both windows and ubuntu? I know when you switch to different CPU architecture windows freaks out but will it matter if the architecture matches? (amd for amd)?

Cheers

I'm not sure how either os would react to a new m/board.
Maybe disconnect your HDD'S and test with a fresh install of ubuntu on an old or unused HDD.

---

### Post by sensay on 2010-01-10
Dont have a spare hard drive unfortunately. I think ill just try it, might learn a little something along the way.

Thanks very much for the advice stinkeye. I have a long day of testing ahead of me, hopefully it will be fruitful.

Cheers

---

### Post by stinkeye on 2010-01-10
> **sensay said:**
> Dont have a spare hard drive unfortunately. I think ill just try it, might learn a little something along the way.

Thanks very much for the advice stinkeye. I have a long day of testing ahead of me, hopefully it will be fruitful.

Cheers
Yes, it's always hard to work out what's causing the problem.Just a process of elimination.
As a note I had the most problems with Psu's until I started buying better quality makes.Good luck.

---

### Post by sensay on 2010-01-10
huzzah!

Motherboard it was. (i think anyway). Managed to keep windows bootable after the motherboard changeover, quickly attempted to load draconis 2 (as the worst behaving game, its easier to notice an improvement here) and the game didnt crash for a solid 20 minutes. Far outshadowing the 15 seconds or so of before. It did run at like 5 FPS though, i reckon thats cos things got borked in the mobo switch. My transfer speeds have improved as well. I noted 20Mb/s before the switch and am now transferring at a happy 35-40Mb/s.

Gonna reinstall now and hopefully everything will stay sorted.

---

