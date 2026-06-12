---
title: "What to use on a old laptop 512MB of Ram"
date: 2012-07-05
forum: General Help
---

### Post by LeftFoot on 2012-07-05
Hi there,

Everything is in the title.

What do you advice for to use on a pretty tough laptop that refuse to die.
It must be 5 or 6 years old with only 512MB of RAM.

Lubuntu ? I read it needs 512MB to run ok, so I am afraid it might be a little close.

Arch + LXDE ?
Any other idea ?

Thx

LeftFoot

---

### Post by papibe on 2012-07-05
Hi LeftFoot.

My personal rule of thumb:
```
P4 -> Xubuntu
P3 -> Lubuntu / Crunchbag / Bodhi
```
Regards.

---

### Post by GreatDanton on 2012-07-06
I prefer Knoppix rather than Lubuntu on very old machines. It's much faster.

---

### Post by claracc on 2012-07-06
I have lubuntu 12.04 in a pentium III laptop CPU 1 GHZ, 512 Mb ram, 64 MB for sis 630/730 graphics card and 20 GB HDD. About 10 years old lapyop. It works very well.

Surfing web with opera 12 and chromium, flash videos in slow motion and consuming 100 % CPU but it is due to the adobe flash plugin.

Playing music with SMplayer and doing office tasks with abiword.

I have tried too, in this old laptop, knoppix from live CD, I think this is a perfect OS for this low specs laptop, the only drawback this is an OS not thought to install in HDD.

I think lubuntu 12.04 has to "fly" in your 6 years old machine

---

### Post by LeftFoot on 2012-07-06
Well actually can't boot Lubuntu : I get a Kernel panic error !! :(

Knoppix is only a live distro right ? I would prefer going for one locally installed.
Never heard of Bodhi before. It has the advantage to be an Ubuntu variant (so no need to learn yet another distro).

I tried #! a lonnnng time ago, and it was pretty neat !
I am sure it will be fast with openbox...

hum... time to make a choice!

Thx for all your answer

LeftFoot

---

### Post by claracc on 2012-07-06
> Knoppix is only a live distro right ? I would prefer going for one locally installed.

Actually you can install knoppix in HDD, but the author says he thought the OS to be run from live CD: [http://knoppix.net/](http://knoppix.net/)

---

### Post by LeftFoot on 2012-07-06
Oh thx Claracc,  didn't know that.

I figure out why Lubuntu crashed during the install : one of the memory module is not working.

I put it off, and installation is under way right now.

The issue is that now I am down to only 256MB of RAM. Not sure how usable will be Lubuntu like this.

I will give it a shot and fall back to Bodhi if it&#347; too slow

LeftFoot

---

### Post by dcstar on 2012-07-06
A large hammer?

---

### Post by mastablasta on 2012-07-06
Lubuntu will be usable. as will be #!, AntiX, Bodhi, Puppy, Slitaz and a few other light distros.

---

### Post by MG&amp;TL on 2012-07-06
> **LeftFoot said:**
> Oh thx Claracc,  didn't know that.

I figure out why Lubuntu crashed during the install : one of the memory module is not working.

I put it off, and installation is under way right now.

The issue is that now I am down to only 256MB of RAM. Not sure how usable will be Lubuntu like this.

I will give it a shot and fall back to Bodhi if it&#347; too slow

LeftFoot

Graphical installation might be...dubious with 256MB, but it should run fine once installed. Ease off on the memory-hungry apps though

---

### Post by black veils on 2012-07-06
> The issue is that now I am down to only 256MB of RAM. Not sure how usable will be Lubuntu like this.
it is a struggle, but with the correct settings it can be made ok. i would recommend Bodhi Linux, it is lighter than Lubuntu, with lots of features and theming choices, the only issue i have is not being able to shrink the giant fonts of applications.

i setup an old laptop for someone to newly explore  Linux operating system, it has 256 ram.
i found that using the web browser Midori can be really good for speed, just dont tweak the settings, it gets unstable then, or in Bodhi it does. choose the Iphone user agent in the settings, because then you will get web pages for the iphone, which is a lot lighter. of course if there is no mobile view for a website, then it will display in desktop mode. i also have the side bar enabled on the left, for access to bookmarks, convenient use of window (due to smaller space needed for iphone web pages), and easy access to manage bookmarks and history.

if you want a full featured web browser, strangely i found firefox is the best for performance, with adblock extension.

i still think Thunar would be a safer file manager then PCManFM, so that is what i am forced to setup. Thunar is nice once is is loaded, and you can always disable the network mount, there will be a broken network link and icon, but it will make first load faster.

make sure you have Preload installed, for apps and functions to load faster once they have already been used in a session. you need to search "readahead" in synaptic for it to show as a result.

and swappiness value should be changed from 60 to 10 (or less, but not zero). i set the swappiness to 2 !

and avoid using the update manager, it is heavy!  use a launcher which runs a script for command-line updates, thats what i did.

---

### Post by MG&amp;TL on 2012-07-06
> **black veils said:**
> 
and swappiness value should be changed from 60 to 10 (or less, but not zero). i set the swappiness to 2 !


Wouldn't that cause it to swap less aggressively (which is good) but use more RAM (which is very bad in this case)? If so, with the OP's current RAM position, I can't see that being a good thing.

Not trying to be negative, the rest of your post was fine. Especially the iPhone tip, I'll remember that one. :)

---

### Post by black veils on 2012-07-06
> **MG&TL said:**
> Wouldn't that cause it to swap less aggressively (which is good) but use more RAM (which is very bad in this case)? If so, with the OP's current RAM position, I can't see that being a good thing.

Not trying to be negative, the rest of your post was fine. Especially the iPhone tip, I'll remember that one. :)

with less ram, it will use the swap more, which causes terrible slow-down. so if you lessen the number for swappiness, it waits for longer before using swap, which means better performance.

---

### Post by MG&amp;TL on 2012-07-06
> **black veils said:**
> with less ram, it will use the swap more, which causes terrible slow-down. so if you lessen the number for swappiness, it waits for longer before using swap, which means better performance.

and when it does, there's no RAM left at all, meaning the next application is ....wait for it...slow. 

Two sides of the same coin I guess, thanks for the explanation.

---

### Post by black veils on 2012-07-06
whilst doing the setup, i have been using the laptop of 256 ram, it does generally run better, there isnt that swap slow-down, thats all i can say.

---

### Post by Lloydb39 on 2012-07-06
Why not add memory? I had an old Dell with 512 meg. I could run Xubuntu or Puppy on it as it was, but I bumped it up to 1 gig and it runs Xubuntu just fine.

---

### Post by mastablasta on 2012-07-07
he is down to 256 and it might be expencive gettign a module for an old mashicne. however if there is a good cheap used on out there on th emarket it might be worthwile.
 
i would upgrade it in an instant but the old mashcine that was handed down has a limit of 384 MB so bleh... not worth the investment. i bought a new battery though, but it went bust after about 2 years.

---

### Post by LeftFoot on 2012-07-09
Yes using a old laptop, not even sure you can find the memory modules anymore.

Just for the record :

- Installing Lubuntu with 256MB was too much for my patience (waited like 20min and were still waiting for the first screen of the installer Oo ! )

-Switch to Bodhi :
+ Installation slow but doable easily (took like 30/40 min in total)
+ System surprisingly fast after that
+ E17 is pretty good looking IMO, but... well... I got used to Unity and miss it :)
+ Flash is not working: nothing is installed by default. They provide a installation process that doesn't work that well in my case.
+ No sound :(   Damn I though that was something of the past in Linux, but since I am using a laptop of the past, maybe that makes sense :)  

So pretty nice over all, but some work to do to make it useable. I will need to spam the Bodhi forums :D


LeftFoot

---

### Post by ronnysingh on 2012-07-09
> **LeftFoot said:**
> Hi there,

Everything is in the title.

What do you advice for to use on a pretty tough laptop that refuse to die.
It must be 5 or 6 years old with only 512MB of RAM.

Lubuntu ? I read it needs 512MB to run ok, so I am afraid it might be a little close.

Arch + LXDE ?
Any other idea ?

Thx

LeftFoot

I used Lucid Lynx on a laptop with configuration of the same RAM and Pentium dual core processor. I never had any problem with speed but I mostly use web browsers and OpenOffice. It worked fine with graphic and video apps too. But I'm not into gaming so can't say anything about that.

---

### Post by black veils on 2012-07-10
Google "bodhi app centre" and then choose one of the full packages. or i can PM you a list of software to install, i can make it one big command. i could also help with recommendations if you get stuck.

---

### Post by mastablasta on 2012-07-10
> **LeftFoot said:**
> Installing Lubuntu with 256MB was too much for my patience (waited like 20min and were still waiting for the first screen of the installer Oo ! )
 
 
for 256MB ram you should use alternate CD. even if you did manage to get graphics installer to work it used to crash during install on 256MB ram.

---

### Post by mojo risin on 2012-07-10
I'd take Lubuntu, it is running fine :) I have got 512 mb RAm as well, :) It is idling on about 150 MB RAM and is on about 250 MB RAM when I use firefox and skype etc.

---

### Post by LewisTM on 2012-07-10
My suggestion: install **zram-config** on X/Lubuntu 12.04
It's a RAM compression scheme that dramatically increases the stability of your system when reaching the limits of your physical memory. It decreases the need for disk swapping which usually brings your system to a crawl, or worse.

Cheers!

---

