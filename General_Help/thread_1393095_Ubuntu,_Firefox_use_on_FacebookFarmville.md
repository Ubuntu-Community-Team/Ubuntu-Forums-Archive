---
title: "Ubuntu, Firefox use on Facebook/Farmville"
date: 2010-01-28
forum: General Help
---

### Post by MaggiesDad on 2010-01-28
I am having processor occupancy going sky high when using Facebook, Farmville. Using Firefox browser. One of my machines crashes all together. Other just gets super slow. This seems to have gotten worse lately. I kind of suspect latest updates but of course don't pay a lot of attention to those when they come up. 
Ubuntu 9.10 Firefox 3.57 HP AMD 2gig, Dell 486 2gig both have 500k mem.

---

### Post by Azyx on 2010-04-13
> **MaggiesDad said:**
> I am having processor occupancy going sky high when using Facebook, Farmville. Using Firefox browser. One of my machines crashes all together. Other just gets super slow. This seems to have gotten worse lately. I kind of suspect latest updates but of course don't pay a lot of attention to those when they come up. 
Ubuntu 9.10 Firefox 3.57 HP AMD 2gig, Dell 486 2gig both have 500k mem.

What is 500k and 2gig?

---

### Post by blur xc on 2010-04-13
> **Azyx said:**
> What is 500k and 2gig?

If I were to guess- 2ghz processors and 500k ram?  Doesn't make sense though.  500k or ram is like nothing.  Maybe 500mb (more likely 512mb)?


BM

---

### Post by Azyx on 2010-04-13
> **blur xc said:**
> If I were to guess- 2ghz processors and 500k ram?  Doesn't make sense though.  500k or ram is like nothing.  Maybe 500mb (more likely 512mb)?


BM

If that is the case (500MB RAM and 2GHz AMD). The f*cking farmville and adobe-flash-player eating memory AND processor power like a cow eating grass ;)
 I have a Core duo 2,3 GHz and after a while mozilla eating up all memory and the processor working at about 60%. If I don't shut down and restart and the memory leak going up to 2GB the system freeze and i havbe to ctrl+alt+F1 and kill mozilla with top.Then I can go back with ctrl+alt+F7 and start mozilla again. I also only have a 1MBits adsl, and that maybe are a problem, couse the network traffic are quite high.

I really want to find a better solution on the problem...

/Cheers

---

### Post by TBABill on 2010-04-13
I think you'll find the problem to most likely be related to Adobe Flash. Do you have the most current? You aren't running 32 bit flash with a 64 bit OS are you? It works, just crappy.
 
I have found most Flash issues are slow performance (jittery on videos, jerky in games, etc) and high heat from your CPU. Flash isn't great for Linux, but some distros work better with it than others. Only experimentation can answer that for you.
 
Search the forums for Flash optimization and you will find a few tips or tricks to try to help you out. There's no quick or easy fix. Higher powered CPUs and systems with more RAM still aren't great in many cases I have found. 
 
Thanks Adobe :)

---

### Post by tuxulin on 2010-04-13
try to test farmville under google chrome or opera if it works better then 
the firefox plugging needs sorting out. 

Tux

---

### Post by blur xc on 2010-04-13
Also- Facebook might have problems as well.  On my computer, I can play flash games on [www.teagames.com](www.teagames.com) flawlessly (tg motocross 3, specifically), at least as good in Ubuntu on the same computer booted into vista, but the same game in facebook is slow, choppy, and un-playable.

:(

My wife gave up on Fishworld because it was causing grief as well.

BM

---

### Post by Azyx on 2010-04-13
> **blur xc said:**
> Also- Facebook might have problems as well.  On my computer, I can play flash games on [www.teagames.com](www.teagames.com) flawlessly (tg motocross 3, specifically), at least as good in Ubuntu on the same computer booted into vista, but the same game in facebook is slow, choppy, and un-playable.

:(

My wife gave up on Fishworld because it was causing grief as well.

BM

Yes, the problem IS Flash, becourse  the memory-leak are also with Chrome, and I think also in XP. I vill check it tomorrow at work.

It's not easy to fix flashplayer, but what I mean is the problem is that when mozilla/flash eating up all memory, the hole ubuntu-desktop freeze (the desktop get greyish)

BM. I will se if It's better on farmville.com..when I get the inlog.

---

### Post by Azyx on 2010-04-14
> **TBABill said:**
> I think you'll find the problem to most likely be related to Adobe Flash. Do you have the most current? You aren't running 32 bit flash with a 64 bit OS are you? It works, just crappy.
 
I have found most Flash issues are slow performance (jittery on videos, jerky in games, etc) and high heat from your CPU. Flash isn't great for Linux, but some distros work better with it than others. Only experimentation can answer that for you.
 
Search the forums for Flash optimization and you will find a few tips or tricks to try to help you out. There's no quick or easy fix. Higher powered CPUs and systems with more RAM still aren't great in many cases I have found. 
 
Thanks Adobe :)

I tested with windos XP, Core 2 Duo 2,5GHz , 2GB RAM and a 1GBit/s LAN and still the processor used 60-70% and the RAM uses little more than 1GB when runing Farmville.Also the swap get around 1GB. So If the user have a AMB 2 GHz and 500MB RAM, that is probably a big reason to the  problem the tread-starter have.

---

### Post by Azyx on 2010-04-16
> **Azyx said:**
> Yes, the problem IS Flash, becourse the memory-leak are also with Chrome, and I think also in XP. I vill check it tomorrow at work.
 
It's not easy to fix flashplayer, but what I mean is the problem is that when mozilla/flash eating up all memory, the hole ubuntu-desktop freeze (the desktop get greyish)
 
BM. I will se if It's better on farmville.com..when I get the inlog.
 
The problem that Ubuntudesktop get locked or hang, when FarmVille eating up all memory was for me, that my swap-partition was not activated: See more here
 
[http://ubuntuforums.org/showthread.php?p=9126943#post9126943](http://ubuntuforums.org/showthread.php?p=9126943#post9126943)
 
 
Cheers

---

### Post by maddg3241 on 2010-04-16
zynga has tones of issues with facebook i get a faster speed at [http://www.farmville.com]("http://www.farmville.com")

if you play mafia wars to it is [http://www.mafiawars.com]("http://www.mafiawars.com")

hope you get it fixed

---

### Post by Azyx on 2010-04-16
> **maddg3241 said:**
> zynga has tones of issues with facebook i get a faster speed at [http://www.farmville.com]("http://www.farmville.com")

if you play mafia wars to it is [http://www.mafiawars.com]("http://www.mafiawars.com")

hope you get it fixed

Hey maddag3241
Yes, Zynga has problems with FarmVille and some problems being betteron FarmVille.com. For instans loading game and neibours...Just tested Farmville.com.  But Farmville.com use the same amount of CPU-power (About 70%) and memory on both WinDos XP and Ubuntu

At Work: Core 2 Duo, 2,5GHz,2GB RAM, 1000Mbits LAN with WinDos XP SP3 on the machine
At home: CoreDuo, 2,5 GHz, 1,7GB RAM, 1Mbits ADSL with Ubuntu 8.04 LST an my machine

And the memory use was about 1GB on both WinDos XP and Ubuntu, but the XP machine always used swap-space (Admins may change it?, but I have not Admin-privileges at work)

My problem with my hanging system was becourse I dident have any swap-space Activated at my Ubuntu and the RAM run out (I have not needed it before I begin play FarmVille, Look at TV and have a lot of tabs and other Apps open)

/Cheers

---

### Post by Jive Turkey on 2010-04-16
I don't play those, or use facebook for that matter but if I were you I would look into getting the latest flashplayer plugin installed and see if that helps.

---

### Post by Azyx on 2010-04-16
[QUOTE=Jive Turkey;9131829]I don't play those, or use facebook for that matter but if I were you I would look into getting the latest flashplayer plugin installed and see if that helps.[/QUOT

Jive Turkey.
Who do need help?

I'a quite sure that the problems, if any are Adobe Flash, or those who develope Farmville-application in flash (Zynga).I'm not any application developer, but 
as I have understand it, Is it very easy to make grafic application in flash AND also very easy to make 'uglyhack" that are very harware-consuming. Farmville need processor-power and memory., and quite a lot for that kind of game (no action) I have on Ubuntu the latest flash, and I'm sure that my emplyers (swedish goverment) have the latest Flash-player installed on WinDos XP. My problem was that i didn't have any swap activated.
MaggiesDad who start the thread was little fuzzy in explaining what kind of hardware he had, and the problem may be that the hardware wasn't enought or maybe also that the swap-space are to small. 
/Cheers

---

### Post by webchannel on 2010-05-14
> **maddg3241 said:**
> zynga has tones of issues with facebook i get a faster speed at [http://www.farmville.com](http://www.farmville.com)

if you play mafia wars to it is [http://www.mafiawars.com](http://www.mafiawars.com)

hope you get it fixed

Farmville link not working,
farmville not working in ubuntu in my internet cafe
am in dual boot, in xp, farmville is working without problem, what to to linux?

---

### Post by Azyx on 2010-05-14
> **webchannel said:**
> Farmville link not working,
farmville not working in ubuntu in my internet cafe
am in dual boot, in xp, farmville is working without problem, what to to linux?

Have you installed flash-player?


for me there is no differens beween windos and Ubuntu with adobes propretarian flash-player.

/Cheers

---

### Post by webchannel on 2010-05-17
> **Azyx said:**
> Have you installed flash-player?


for me there is no differens beween windos and Ubuntu with adobes propretarian flash-player.

/Cheers
  already installed flash player but all my 15 dual boot pc not working...

---

### Post by blortuga on 2012-08-28
Flash/AIR have had some issues with garbage-collection within their runtime. Supposedly these were fixed in 3.x (AIR), but the new API required an SDK update (paid), so some developers could not take advantage of that. It's also a bit of a chore to figure out where to insert the new methods to free up unused objects.  I suspect that this is why Flash/AIR may leak some memory after extended use, and NOT allow it to be paged to swap.

This is pretty much speculation though - in order to really know the cause of your problem, you'd need access to the source code and a flash-debug environment to see where memory is not being paged-out or freed. And for a proprietary app like farmville - - - well, good luck with that. :)

---

