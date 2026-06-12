---
title: "Jaunty Repositories: Have you seen me?"
date: 2011-06-07
forum: General Help
---

### Post by adc on 2011-06-07
Hello,

I am trying to install the build-essential package on my new Jaunty install, but I seem to get 404 Not Found for all the repositories.
I have tried main repositories, US ones and the ones recommended in Software Sources as being the best choice, but I get the same response.
I can't install any packages because of this. Could someone help me find the repositories for this distro?

Thank you for reading this thread.

PS: I need to use Jaunty, so updating or using other distributions are not acceptable solutions for me.

---

### Post by Enigmapond on 2011-06-07
To my knowledge, there are no repos for jaunty since the end of life. You would be best to do a fresh install of a newer distro. Why is this not "acceptable"? There is no more support for Jaunty so it won't be safe to use.

---

### Post by adc on 2011-06-07
> **Enigmapond said:**
> To my knowledge, there are no repos for jaunty since the end of life. You would be best to do a fresh install of a newer distro. Why is this not "acceptable"? There is no more support for Jaunty so it won't be safe to use.

This is good to know. I guess I have to rethink my choice, don't I? I kinda needed Jaunty because I had some work already done using it, and I wanted to rather continue than start all over again.

Thank you very much for the quick reply!

---

### Post by lagerratrobe on 2011-07-22
Just to add some context for why these repos are still needed.  Many of the VPS hosting companies are still providing 9.04 as their "Ubuntu OS".  It's a pain not having any packages available from the release when you're trying to setup something on one of them.

[5 minutes after posting this I found another thread in the forums with the answer - "try replacing archive.ubuntu.com with old-releases.ubuntu.com in your sources.list". I did, and it worked.]

Roger

---

### Post by dmrkonjic on 2011-08-05
Yyyyyeeeeeeessssssss

 "try replacing archive.ubuntu.com with old-releases.ubuntu.com in your sources.list". I did, and it worked.

---

### Post by coffeecat on 2011-08-05
> **lagerratrobe said:**
> Just to add some context for why these repos are still needed.  Many of the VPS hosting companies are still providing 9.04 as their "Ubuntu OS".  It's a pain not having any packages available from the release when you're trying to setup something on one of them.

It needs to be said that enabling the old-releases repository is putting the cart before the horse in this situation. Jaunty is an obsolete and unsupported operating system. No security patches have been released since it went eol in October last year. Any company that provides VPS hosting with an unsupported, obsolete OS is acting unprofessionally, in my opinion. It it was my virtual private server I would choose to use a company that at least appeared to be competent.

---

### Post by dmrkonjic on 2011-08-05
> **coffeecat said:**
> It needs to be said that enabling the old-releases repository is putting the cart before the horse in this situation. Jaunty is an obsolete and unsupported operating system. No security patches have been released since it went eol in October last year. Any company that provides VPS hosting with an unsupported, obsolete OS is acting unprofessionally, in my opinion. It it was my virtual private server I would choose to use a company that at least appeared to be competent.


Thanks for your valuable lecture... 
Some of my hardware is working on 9.04 only ... would you be so kind to pay me for a new

I do not understand how 910 is considered as sported if it is still full of bugs and if it can't recognise hardware recognised by 9.04.

---

### Post by coffeecat on 2011-08-05
> **dmrkonjic said:**
> Thanks for your valuable lecture... 
Some of my hardware is working on 9.04 only ... would you be so kind to pay me for a new

No. If your hardware cannot run a later supported version of Ubuntu then that is unfortunate. That, however, does not excuse "professional" server hosting companies from running an obsolete OS.

> **dmrkonjic said:**
> I do not understand how 910 is considered as sported if it is still full of bugs and if it can't recognise hardware recognised by 9.04.

9.10 is also end-of-life.

---

### Post by dmrkonjic on 2011-08-05
> **coffeecat said:**
> No. If your hardware cannot run a later supported version of Ubuntu then that is unfortunate. That, however, does not excuse "professional" server hosting companies from running an obsolete OS.



9.10 is also end-of-life.


Yes, but 10 is even worse with bugs and lack of apps ...  of cours they are better as platforms, but I do not understand why newer can't run previous apps and hardware

---

### Post by 3rdalbum on 2011-08-05
> **dmrkonjic said:**
> Yes, but 10 is even worse with bugs and lack of apps ...  of cours they are better as platforms, but I do not understand why newer can't run previous apps and hardware

What "previous apps"?

As for hardware, the vast majority of what works in 9.04 and 9.10 also works in 10.xx and 11.xx versions. Only on occasion does something break; and where's your bug report saying that Ubuntu 10.04 breaks support for once-working hardware?

---

### Post by dmrkonjic on 2011-08-05
> **3rdalbum said:**
> What "previous apps"?

As for hardware, the vast majority of what works in 9.04 and 9.10 also works in 10.xx and 11.xx versions. Only on occasion does something break; and where's your bug report saying that Ubuntu 10.04 breaks support for once-working hardware?


Apps from 9.04 repo... when I installed 9.10 there was no offer for some applications  I used before, and some of them use to have bugs (like searchmonkey - veeery useful tool) ... 
... and there is no bug report for hardware - 9.10 is just not recognising my USB DVB-T, and my acer 3810TG still can't wake up after suspend  (on 9.04 wakes up..)

May be it's not big deal, but question is why... why to stop supporting old OS before new one is not completely finished.

---

### Post by coffeecat on 2011-08-05
> **dmrkonjic said:**
> 9.10 is just not recognising my USB DVB-T

That's not a bug. That's because in 9.10 (and all later releases) firmware for some DVB-T cards was split off into the linux-firmware-nonfree package. In 9.04 and before all the firmware was included in a default installation. In 9.10, the linux-firmware package was included but not the linux-firmware-nonfree package. This for licensing reasons. You can install linux-firmware-nonfree from the multiverse repository in 9.10 and later versions. Of course, for 9.10 you'll now have to use the old-releases server.

---

### Post by dmrkonjic on 2011-08-06
Thank you vermy much (even I'm not sure if I understand everything - do you want to say there is simple solution?) , then I'll reformulate my complainant: "WHY NOBODY WARN ME, AND HUNDREDS OF OTHER USERS ABOUT THAT???" 

Can you explain to me how to fix a problem - to make it work?

---

### Post by coffeecat on 2011-08-06
> **dmrkonjic said:**
> I'll reformulate my complainant: "WHY NOBODY WARN ME, AND HUNDREDS OF OTHER USERS ABOUT THAT???" 

You were warned - it was in the release documentation for 9.10, although you weren't the only one to have missed it. I missed it too - at first. But why the Ubuntu development team didn't send you (and me - and hundreds of others) a personal email about this, I have no idea! :wink:

If you need help with specific problems I suggest you start your own thread. This one is about Jaunty repositories and we've already gone off-topic. However, if you want help with Karmic/9.10 you will inevitably get people commenting that it's unsupported now.

Good luck with that!

---

### Post by Frogs Hair on 2011-08-06
I have not ever used this , but it may be worth taking a look at .
[http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html](http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html)

---

### Post by 3rdalbum on 2011-08-06
There we go, problem solved. Install that package and you'll have the firmware for your stick.

I'd disagree with your comment that "there's no bug report for hardware". If hardware compatibility regresses unexplicably, then you need to report it. Most drivers live in the kernel, so report driver bugs against the kernel (except for things that you know are the responsibility of other packages, such as HP printer drivers). If you've reported a hardware support regression against the kernel when it should go somewhere else, a triager should be able to recognise this and move it for you.

---

### Post by dcstar on 2011-08-06
> **coffeecat said:**
> You were warned - it was in the release documentation for 9.10, although you weren't the only one to have missed it. I missed it too - at first. But why the Ubuntu development team didn't send you (and me - and hundreds of others) a personal email about this, I have no idea! :wink:


"Unsupported" means no patches when critical security issues are identified, so anyone running an "Unsupported" release of Ubuntu has their systems wide open to attack from any security threat that has arisen since those releases became "Unsupported".

Anyone using an "Unsupported" release is therefore using an insecure system.

Unfortunately Ubuntu (and every single other O/S) relies on people actually reading the documentation for each release and understanding what the implication are - a big issue for some people, apparently.

If people are concerned about releases being supported for a long time, I suggest they investigate what "LTS" means:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by hrimhari on 2011-08-07
> **dcstar said:**
> "Unsupported" means no patches when critical security issues are identified, so anyone running an "Unsupported" release of Ubuntu has their systems wide open to attack from any security threat that has arisen since those releases became "Unsupported".

Anyone using an "Unsupported" release is therefore using an insecure system.

Unfortunately Ubuntu (and every single other O/S) relies on people actually reading the documentation for each release and understanding what the implication are - a big issue for some people, apparently.

If people are concerned about releases being supported for a long time, I suggest they investigate what "LTS" means:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

All valuable tips. BUT... Sorry, it's rant time.

There is a class of users (original poster and me included) which suffers with every Ubuntu upgrade. Maybe it's because we have "unusual" hardware and maybe because we're a minority.

It does take about a week, sometimes more, to get my laptops/tabletpc working to something closer to their full potential.

It happened more than once that a certain release missed support for one hardware which was added to the next release, but when I upgraded I lost support to other hardware.

I used to stick to LTS thinking they would have general support for longer, not only extended security fixes. What I mean by general support is, hardware which is missing support will be added during the version's lifetime. This is not what happens.

While in Hardy, I managed to get the pen working flawlessly, but the screen rotation was not supported. Support was added to Jaunty/Karmic.

When I upgraded to Karmic, there was NO WAY to make my tabletpc's wireless work. I tried every suggesstion I could find on the forums. Non-free driver, ndiswrapper, uninstall-reboot-reinstall-reboot, what have you. I had to downgrade to Jaunty to have it back working. But I can't use the pen's buttons.

In Dapper, I could put my GNOME bars vertically aligned (which is mandatory on wide screens) without any problems. When I upgraded to Feisty, the applications bar started to freeze my X environment when I got 7 windows opened. To my knowledge, after 10+ releases this bug has not been fixed.

That considered, I'm willing to have a somewhat less secure system if it will save me the "10 new problems for every one fixed" tragedy.

All that said, I do cherish the Linux experience due to the freedom it gives me to have the chance to solve my problems myself. What I'm saying is, when you go popular, you get an entire class of users which wants things to "just work". Sorry, but that's not the experience I (and the original poster) have, and it does increase the rants.

---

### Post by dmrkonjic on 2011-08-08
> **hrimhari said:**
>  

There is a class of users (original poster and me included) which suffers with every Ubuntu upgrade. ...



That's the point++++ 
(I started in 1986 with Commodore 64, but ) my first business machine come in 1994 - 486 33mhz (and - believe it or not - I'm still ruining my accounting on it under MS DOS, and P200MMX with W98 is still my "typewriter" because one of my printers (excellent) Canon LBP800 can't work on XP) 
From that time programmers are coming to me with new "better" releases every year, and than I need next three months to get used on it and they need same time to fix bugs... but I'm living of my business not of hacking, gaming and training on new programs... (I quit with them in 1998. and I'm still using old release --- nothing new invented in in double-entry bookkeeping for hundered years !!! )

YOU SEE... HYGIENE IS GOOD, BUT IF YOU TAKE SHOWER, AND CHANGE UNDERWEAR EVERY SINGLE HOUR, AND IF YOU WASH HANDS EVERY FIVE MINUTES, YOU HAVE NO LIFE ANY MORE, SO THERE IS NO NEED FOR HYGIENE ANY MORE   ...
SAME IS WITH SOFTWARE - IT SHOULD SAVE OUR TIME, NOT TO WASTE IT 
OS SHOULD BE, NOT ULTRA MODERN AND EVERY DAY UPDATED, BUT STABLE AND RELIABLE ... AND IT SHOULD RUN MUCH AS POSSIBLE OF A HARDWARE AND APP''S

---

### Post by CatKiller on 2011-08-08
There are very many rolling release distros out there. Ubuntu isn't one of them.

---

### Post by dmrkonjic on 2011-08-09
> **CatKiller said:**
> There are very many rolling release distros out there. Ubuntu isn't one of them.


??? It is the story about suffering of upgrades...
I'm running U9.04 & 9.10 (because 9.10 is not only upgrade, it is partly downgrade of 9.04, and these is common problem of (always) premature software

---

### Post by WorMzy on 2011-08-09
If your hardware isn't supported by the default Ubuntu kernel, consider compiling your own.

---

### Post by dmrkonjic on 2011-08-09
> **WorMzy said:**
> If your hardware isn't supported by the default Ubuntu kernel, consider compiling your own.

It is not about unsupported hardware...my hardware was supported, but it is not after upgrade (and it is downgrade for me) and I waste days and nights in attempt to fix the problem - and finally I'm switching between 9.04 and 9.10

And, sorry I'm not able to compile anything, and I'm not complaining - because Linux is free, so I'm grateful... 

and I want to help somehow - I can't help in compiling because I'm not programmer, but I can help with advice what should be good for many people (because I'm working on 5 computers in 5 different OS at the moment,  so I understand the problems of common user.

---

### Post by imnotrich on 2012-04-10
> **WorMzy said:**
> If your hardware isn't supported by the default Ubuntu kernel, consider compiling your own.

If I was running some obscure or uncommon hardware, compiling my own kernel would be one thing. 

But for common, current, recent vintage hardware? I don't think so! 

I found this thread searching for the 9.04 repos also, because later versions of Ubuntu do not support my laptop's very common ATI radeon card nor it's Realtek 8185 wifi card. In fact all the major distros from the last two years or so do not support this hardware. And yet people are still buying laptops with this hardware in them - so what's the deal? 

Hardware support is not bloat, and for many distros bug reporting is a placebo only. Nobody looks at your report, or the response is some snide comment like "compile your own if you don't like it." 

Like the OP I am not in the position to buy a new laptop every year. Backwards compatibility, at least for hardware, should be important to every distro but seemingly it's not. 

Why is that?

---

