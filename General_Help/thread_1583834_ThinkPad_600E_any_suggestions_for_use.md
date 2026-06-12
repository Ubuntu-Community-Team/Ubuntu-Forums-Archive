---
title: "ThinkPad 600E: any suggestions for use ?"
date: 2010-09-28
forum: General Help
---

### Post by astrobob.tk on 2010-09-28
I still own an IBM ThinkPad 600E which has been collecting dust for years. Does anybody have any suggestions for its use ? I searched IBM's page for it using the tag & you can access it [here]("http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2645550").

[B]Additional stuff you should know:
[/B]
1. The system always shows 2 or 3 error when turned on. The errors are 161, 163 & 173. I checked this page for the meaning, & I think its a result of the battery which is not charging. Not sure if its the batt or the adapter with the problem.
Note that when I get the errors & press OK, I reach this:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=6783[/IMG]

All I understand from this is that I should turn off the computer & then on again.

2. I have Windows Me on it.

2. I tried Debian 5.0.1 "Lenny" from a dual-layer DVD I got along with a linux magazine & its loading. It reaches the installation process though not always. It sometimes freezes at "ISOLINUX 3.71 Debian-2008-09-06" before loading the menu.

Any help, suggestions or ideas ?

thanks

---

### Post by ajgreeny on 2010-09-28
If the machine has Windows ME on it, I suspect there is only a max 256MB of ram, insufficient to run properly, and certainly to install a linux Distro of the size of any of the ubuntu family, except perhaps **lubuntu**, with the lxde desktop.  Actually you may get some to install, but they will creep along very slowly.

What is the hardware in the laptop?

---

### Post by held7over on 2010-10-17
Hi astrobob.tk!  

I have been running Ubuntu on a 600e and 600x Thinkpad since Ubuntu 8.04. It runs great, with one exception of a sound problem on the 600e, which we used to have a fix for, but the file structure has changed in 10.04 (see below) and I am no longer sure of how to make the necessary changes. (I have supplied a URL with a copy of the fix on it. You can google for more versions of it.)

Sure, it is not super fast, after all, it is only a Pentium III, but it is still very usable if you have a little patience. Memory is cheap. You can boost your 256 MB of ram up to 288 MB of ram and it does make a speed difference!

Here is what your errors mean:

161  Dead Battery  (backup battery)
163  Time and Date were not set
173  Configuration Data was lost

All these errors come from one simple thing. Your little backup battery is dead. This is an easy to get to CMOS battery. You just unscrew the plate on the bottom and gently ease it out and swap it. It has a tiny white connector with a red and black wire, it may be orange or yellow and flat like a dime. Just google for "CMOS Replace Thinkpad 600e".  You can purchase a new one for about $1 on ebay by searching for "CMOS Thinkpad 600e" and you will be in business.

(Note: After replacing the CMOS battery, if you still get an error, there is also a tiny button battery, (I am thinking it is near where you insert more ram) that you might want to also replace! Again, it is super cheap to do so.)

The only problem you will have, is, on the 600e the sub-manufacturer of the sound card used the wrong chips! As a consequence, sound will not naturally be working on the 600e after the install.  There is a fix for this that worked all the way up to and including Ubuntu 9.10, but unfortunately it appears the file structure of the sound areas has dramatically changed in Ubuntu 10.04, and I haven't been able to figure out what part of the fix goes where in that expansion. But here is the old fix. If you or someone else figures out how to apply this in 10.04 and higher, please update this thread!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/40116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/40116)

On any 600 Thinkpad, you may also now have problems playing some or all movies...maybe...and this seems to be related to changes that make movie playing much more of a ram hog....or it has to do with something they have added that is using a lot of processor power...as in 8.04 and 8.10 movies had no problems at all.  (There may be an answer for this, I haven't researched it that much yet.)

Before you install...You will need to go into the bios and tell it to first look at your cd or dvd to boot up from, before looking for a bootup from hard drive....and while you are there, you should disable FASTBOOT.

I hope this helps!

---

### Post by astrobob.tk on 2011-03-29
Thanks guys for the reply. Its been quite a while since i checked this thread. Just now I was attempting (before reading your replies) to boot Knoppix 6.5 from my 8GB USB. Apparently Knoppix managed to initialize but hanged somewhere due to some hardware issue I believe; i didn't delve much into it, I just though i'd give it a try.

Anyways, indeed I have Windows ME on it & i just extracted the following data from "dxdiag":

> system model: 2645550
Bios: IBM
Processor: Intel Pentium II, MMX. ~300MHz
Memory: 64MB RAM
Page file: 69MB used, 1915MB available

Display: NeoMagic MagicMedia256AV
Approx. Total Memory: 2.5MBApparently, its not even 128MB RAM lol.

I recall taking images of the errors that usually occur (i guess they are due to the CMOS as you mention) but can't recall where I located them. I will upload them when i find them.

In the meantime, do you suggest any linux distro that might be better than Win ? Of course as you mentioned Ubuntu is way heavy for such a device; even my desktop computer which has 256MB RAM & 1.0 GHz cpu couldn't handle Ubuntu; I managed to install Debian 5.0 which performs quite slow.

---

### Post by held7over on 2011-03-29
Yes! I can suggest a light weight linux that will run great on the 600 series and run faster than the original Windoz 95.

Get DSL (Dam Small Linux) it is based off of knoppix but installs as debian if you put it on your hard drive. Grab the live CD and try it out!  It takes up a whole 50 mb of ram.

Puppy Linux is pretty cool also, in the same size range, with the same fast response times, however I haven't tested it on my 600e because my daughter now has that several hundred miles away....and may not return it!  And on my 600x it boots but runs into a "uncompression problem" in unpacking stuff. It may be just an corruption on my cd, but it boots in other machines...so, it may be worth grabbing that also and trying it.

Either one you pick, I think you are going to be pleased with...if speed is what you are looking for. :P

---

### Post by held7over on 2011-03-29
Go with Damn Small Linux (DSL). 

Evidently the newest version of Puppy has larger RAM needs, see 

[http://www.murga-linux.com/puppy/viewtopic.php?t=60480&sid=0fb180ab022e30d03b6b796b0a15bbef](http://www.murga-linux.com/puppy/viewtopic.php?t=60480&sid=0fb180ab022e30d03b6b796b0a15bbef)

---

### Post by astrobob.tk on 2011-03-30
> **held7over said:**
> Go with Damn Small Linux (DSL). 

Evidently the newest version of Puppy has larger RAM needs, see 

[http://www.murga-linux.com/puppy/viewtopic.php?t=60480&sid=0fb180ab022e30d03b6b796b0a15bbef](http://www.murga-linux.com/puppy/viewtopic.php?t=60480&sid=0fb180ab022e30d03b6b796b0a15bbef)

Thanks held7over, i will definitely consider all this; maybe I will put some time on it this summer

Note though that DSL's page also says "Run fully in RAM with as little as 128MB"

---

### Post by Rasa1111 on 2011-03-30
I have the same machine!
Still works also.
 Used to have XP on it,
Now it has Lubuntu 10.04.

and it actually runs 'fast'! lol

Thing is like 13 years old.

It was the only thinkpad i had until a month or so ago,
Now I have a newer one (Z61t), and it's amazing. :o <3 lol

The old 600E is a beast though.
Old as it is, weak as it is...
Still boots up super quick, runs quick, smooth, etc.

Id suggest Lubuntu. ;)

Mine has a 6 GB HDD and 144 RAM. :lol:

Funny enough, a puppy disc (lucid puppy) won't even start up on it. lol

 the hard drive is pretty much shot though.
Could go at anytime.
might replace it one of these days. :???:

I don't really use it though. 
Can only connect with dial up...
and it cant play big files well..
So its good for writing, music, reading ebooks, things like that...i guess.

heres a pic of both of them side by side..
600E is running spinrite6 here. 
I dont have a shot of it booted up into lubuntu tho, so you jus gotta trust me. lol

---

### Post by held7over on 2011-03-30
Nice picture Rasa1111!

I haven't tried lubuntu. 

Is it's connection manager as automatic for switching between hardwired and wireless as ubuntu's manager? Perhaps the same one?  (I ask because my wife needs all the help she can get when she travels with the laptop! :) )

---

### Post by Rasa1111 on 2011-03-30
> **held7over said:**
> Nice picture Rasa1111!

I haven't tried lubuntu. 

Is it's connection manager as automatic for switching between hardwired and wireless as ubuntu's manager? Perhaps the same one?  (I ask because my wife needs all the help she can get when she travels with the laptop! :) )

Thanks mate, :)

 You know..
to be honest.. I'm not quite sure... lol
Since the machine only has a dialup (telephone) jack,
I dont really ever connect it..

But, I will pop the disc into this laptop in a little while and check it out for you, then write back here. 

Good question, Now I also want to know.. lol
I think it is though.... :)

edit: oh wow, Just noticed i missed astro bobs post with the "64MB RAM" yikes!
hmm...

not sure if lubuntu will run on 64 MB..
runs fine on my 144 mb tho.. lol

---

### Post by held7over on 2011-03-31
I burned a Lubuntu cd and tried to boot my 600x Thinkpad with it. That machine has about 328 MB RAM. However, each time it came to the TRY or INSTALL menu, after I had hit either TRY or INSTALL, it went to a black screen and ended up rebooting. I couldn't get any farther, which is weird, since you are running it in 128 MB.

I then tried it on a P3 desktop with a bit over 750 MB and it ran like a champ breathing new life into the thing!

There is something it just didn't like about my 600x. I may try the lubuntu forum to see if they have an solution. I think my wife would really like it...

Thanks for putting me on to it.

---

