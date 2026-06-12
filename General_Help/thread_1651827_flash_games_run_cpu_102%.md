---
title: "flash games run cpu 102%"
date: 2010-12-23
forum: General Help
---

### Post by Dopaque on 2010-12-23
The browser doesn't seem to matter--firefox, chrome, seamonkey, epiphany... no matter what, when I run flash games (esp. the neopets habitarium game), the cpu runs really hot. Nothing freezes, but I haven't tried having anything else open, either.

I have adblock blocking most flash ads and then flashblock to get rid of al flash period, and no other add-ons. Flashblock got rid of a lot of cpu spiking on other pages... but what do you do when you WANT flash to work?

I've tried gnash; doesn't work. I've tried downloading the plugin from adobe; doesn't work. I tried the nonfree plugin; doesn't work. They all get the same abysmal cpu usage with intensive flash.

I'm running the newest firefox beta, but again, the browser doesn't seem to matter.

How can I get flash working without eating up over 100% of my cpu??

---

### Post by akand074 on 2010-12-23
Have you tried removing every single flash you have installed completely. And then just install the flash from the Adobe website. That's pretty impressive.. over 100% CPU. Also pretty comical, flash induced over-clocking haha. Are you using a 32 bit OS or a 64 bit OS? Also are you still in 8.04 as your information states?

---

### Post by mikewhatever on 2010-12-23
You can't do anything about it. Just wait for Adobe to make flash on Linux more efficient and provide hardware acceleration. The question is, will they do it anytime soon, so that it actually matters.

---

### Post by akand074 on 2010-12-23
> **mikewhatever said:**
> You can't do anything about it. Just wait for Adobe to make flash on Linux more efficient and provide hardware acceleration. The question is, will they do it anytime soon, so that it actually matters.

That's just silly. I had flash running on Ubuntu for two years without issues on several computers. I'm sure the OP didn't always have this issue, otherwise he would have mentioned that, or even more likely posted about it in the past seeing as he's been using Ubuntu since at least 8.04.

---

### Post by endersbean3k1 on 2010-12-23
I always found that flash sucked up a ton of CPU... it is a relevant question to ask: what hardware is OP using? It could just be that flash uses that much CPU.

---

### Post by mikewhatever on 2010-12-23
> **akand074 said:**
> That's just silly. I had flash running on Ubuntu for two years without issues on several computers. I'm sure the OP didn't always have this issue, otherwise he would have mentioned that, or even more likely posted about it in the past seeing as he's been using Ubuntu since at least 8.04.

Silly or not, I don't want to make assumptions. Just consider that running flash on Linux and flash efficiency on Linux are not the same thing. Perhaps you could run the games the OP complained about and report the findings.

---

### Post by akand074 on 2010-12-23
> **mikewhatever said:**
> Silly or not, I don't want to make assumptions. Just consider that running flash on Linux and flash efficiency on Linux are not the same thing. Perhaps you could run the games the OP complained about and report the findings.

Well reproducing the error would definitely push the blame toward flash itself. It's no secret that flash is resource intensive, but that's overkill unless he is on ancient hardware. Also if that problem didn't occur on similar level content in the past then that pushes the blame away from flash itself. I'm just saying we shouldn't jump to a conclusion until we have more detail like what Ubuntu release he is using, 32 bit or 64 bit, what his hardware is like, whether the problem always occurred or whether it was once not a problem, and any other relevant information.

---

### Post by mikewhatever on 2010-12-23
Fare enough, so please, don't jump to conclusions. ;)

---

### Post by akand074 on 2010-12-23
> **mikewhatever said:**
> Fare enough, so please, don't jump to conclusions. ;)

Fair enough. And neither should you, or anyone really ;)

Lesson learned, now if only everyone else in the forums can handle disagreements this maturely.

---

### Post by Dopaque on 2010-12-24
hey, sorry, I'm actually using 32-bit Karmic Koala, with every update so far without upgrading. 

this is an HP Pavilion dv6700 Notebook PC with 3 gigs memory, 2GHz cpu, with a nVidia MCP67 High Definition Audio card and a nVidia C67 [GeForce 7150M / nForce 630M] graphics card using the version 173 driver because the recommended (185) did weird things to my display. I can show the results of "lshw" if you need more information on that.

I've had trouble with laggy firefox and laggy rhythmbox before, but not overclocking on a regular basis.

My computer really isn't that old! And it can run graphics-intensive computer games like Fable on the windows partition, so it shouldn't be hardware that is giving me this problem.

If you want to test the game, I think you need a neopets account, but it can be found at [http://www.neopets.com/habitarium/](http://www.neopets.com/habitarium/). I think any modern complicated flash game would also do the same thing, though. I'll try to find another game or website that overclocks my machine.

EDIT1

found another bit that overclocks my machine, where you could test yours: [http://www.neopets.com/faerieland/](http://www.neopets.com/faerieland/) does it every time. Bit faster in chrome than firefox, but not much.

EDIT2

completely removed everything from synaptic that could be found when searching for "flash" (I had nonfree installed at the time, and gnash). Installed the APT from the adobe website. Ran the game. Still getting in-between 99 and 104% cpu when I play it. And now it's lagging a little when I close it down.

---

### Post by mikewhatever on 2010-12-24
Hey Dopaque, thanks for the update. Unfortunately, the Linux version of flash is much less efficient then its Windows brother on the same hardware. You might be better off playing those games on Windows after all, since there is really nothing you can do about flash.

PS: Try this Linux hack, just in case.
[http://www.ubuntumini.com/2009/11/improve-adobe-flash-performance.html](http://www.ubuntumini.com/2009/11/improve-adobe-flash-performance.html)

---

### Post by akand074 on 2010-12-24
> **Dopaque said:**
> 
found another bit that overclocks my machine, where you could test yours: [http://www.neopets.com/faerieland/](http://www.neopets.com/faerieland/) does it every time. Bit faster in chrome than firefox, but not much.


Holy crap. I just opened that page and my CPU usage jumped to 20% and sustained at around 15-20%, I tried clicking on an area but it said you need to login to do that. Either it is flash that is just a disaster, or they should hire a new programmer. Your hardware on your laptop isn't bad at all either. You can try limiting the amount of CPU that npviewer.bin can use using [cpulimit]("http://www.howtoforge.com/how-to-limit-cpu-usage-of-a-process-with-cpulimit-debian-ubuntu"). Though I would imagine that would lower performance.

I just tried a [game]("http://www.albinoblacksheep.com/games/missilegame3d") I used to play in class back in the day. Just opening it and going through the menu has my CPU usage at 1-2%, once I'm in the middle of a game its up to ~5-8%. Which is still pretty high for such a minor game. I conclude that flash is ridiculously intensive, though I'll also throw some blame at the developers I'm sure they could have developed it a little better.

---

### Post by Dopaque on 2010-12-25
I'll submit a bug report to the site telling them that those particular flash pages/games are extremely cpu intensive, but I doubt that they'll do anything about it.

Surely, though, on a good machine like this, even flash shouldn't *overclock* my box? ...I kind of hate flash now, and how addicted to it I am.

Since I doubt overclocking my machine on a regular basis is a good thing, what cpu cap should I put using that link you gave, akand? something reasonably high that will still help protect my machine? I don't mind if this particular game runs slow or laggy because it is not a reflexes-oriented game at all.

I tried the hack mike gave, and I'm sure it'll help with flickery youtube videos, but it doesn't help with the cpu. Anyone have any more potential help? TT_TT

---

### Post by ben2talk on 2011-01-20
Flash IS resource intensive. It is streamlined for Microsoft, and so if you're playing these games - for me it's facebook games - you'll notice that with Ubuntu, the CPU is being used. Switching to my friend's laptop gives an excellent improvement as Flash is designed for Windows, and I can run the games full screen - dragging maps around is smooth. With Ubuntu, full screen is a real no-no.

Flash is for the masses, and Ubuntu is not going to receive the same level of attention...

Try running a virtualbox, or browser under Wine - any better?

---

