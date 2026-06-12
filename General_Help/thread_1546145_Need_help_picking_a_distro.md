---
title: "Need help picking a distro"
date: 2010-08-04
forum: General Help
---

### Post by hunterkasy on 2010-08-04
I have a old compaq Celeron 466mrz with 64mb of memory,  I know it is really old, but I have this friend who is 50, he is determined to get it up and going again, you know because back in the day it was the fastest on the market, I have been unable to explain that the good old times are a little different from today, SO I am wondering what Linux distro would be the best for that slow of a machine?

---

### Post by snowpine on 2010-08-04
A computer that old will be useless for many of the daily tasks we take for granted in the year 2010 (Youtube, Facebook, OpenOffice, etc.) regardless of the distro.

That being said, there are still some fun projects you can do with an old computer. Here are some ideas: [http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)

---

### Post by jmszr on 2010-08-04
hunterkasy,

You should find something that will work for you here: [http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/) .

Edit: Or here: [http://www.linux.com/news/hardware/desktops/8248-linux-distros-for-older-hardware](http://www.linux.com/news/hardware/desktops/8248-linux-distros-for-older-hardware)

---

### Post by HPD2 on 2010-08-04
You could give [crunch bang]("http://crunchbanglinux.org/") a try, it is a great lite weight distro.

---

### Post by snowpine on 2010-08-04
CrunchBang would be a fantastic choice if you can up the RAM to 256mb+.

Honestly I can't think of a single modern distro (edit: maybe tinycore or the 'loram' flavor of slitaz?) that will run well with only 64mb of RAM. DSL could, but it is 2 years out of date. With only 64mb you are basically limited to text mode only, maybe a torrent slave or something. :(

---

### Post by Zorgoth on 2010-08-04
Chrome OS is basically supposed to be just a browser.  Maybe it could do it?  I don't know.  I also don't know what stage of development it is in.

---

### Post by UncleNinja on 2010-08-04
[QUOTE=Zorgoth]Chrome OS is basically supposed to be just a browser. Maybe it could do it? I don't know. I also don't know what stage of development it is in.[/QUOTE]
You can try out Flow, a custom build of Chromium OS:
[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

I have no clue if it would work, but it's possible.

EDIT: Yeah, building Chromium OS from the source requires a 64-bit system and looks like a lot of work: [http://dev.chromium.org/chromium-os/building-chromium-os](http://dev.chromium.org/chromium-os/building-chromium-os)

EDIT #2: There's also Strats0s, but I don't know if that's bogus or not: [http://www.stratus0s.org/](http://www.stratus0s.org/)

---

### Post by BenAshton24 on 2010-08-04
Damn Small Linux should work fairly well... or Puppy Linux.

---

### Post by ronnielsen1 on 2010-08-04
DSL advertises it will work on a 486 with 16 M of ram. I don't know about puppy

> I have a old compaq Celeron 466mrz with 64mb of memory, I know it is really old, but I have this friend who is 50, he is determined to get it up and going again, you know because back in the day it was the fastest on the market,

I was very proud of my blazing fast 486 with my gigantic 200 M Hard drive that I bragged to the wife I would never be able to fill up.
I still have that hard drive Reminds me of that comment. It's about 5 inches tall and holds about 130 M of software including DOS 6.22, Win 3.11 for Workgroups, MS Works, MS Word, and tons of games including Doom. I think we bloated out after that

---

### Post by orky7 on 2010-08-04
as mentioned in previous posts you can use damn small linux and one good thing is that once u install Advanced Packaging Tool (APT) you can install packages from debian repository.

---

### Post by compiz addict on 2010-08-04
Try Lubuntu. It's a lite version of Ubuntu using LXDE (Lite X11 Desktop Envionment). It also has a netbook style session and an Openbox only session.

---

### Post by akester on 2010-08-04
I found Fedora with KDE to be decent on a similar system.  It isn't great but it works.

---

### Post by ronnielsen1 on 2010-08-04
The only thing about DSL is it's not being maintained anymore. If you could do research or have the know how a lightweight net install of debian with icewm or jwm window manager would give you a more up to date system

 [http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

This is an old how to but it should give you an ides

[http://www.howtoforge.com/perfect_setup_debian_etch](http://www.howtoforge.com/perfect_setup_debian_etch)

---

### Post by metalf8801 on 2010-08-04
I would try Puppy Linux first 
[http://www.puppylinux.com/index.html](http://www.puppylinux.com/index.html)

also I would look on Distrowatch for distros that run on old computers and are still active 
[http://distrowatch.com/search.php](http://distrowatch.com/search.php)

I hope this helps 
Dan

---

### Post by fredbird67 on 2010-08-04
If you've only got 64 MB of RAM on there, you're pretty much screwed.  You need to upgrade the RAM in the system to at least 256 MB if possible, or else websites like YouTube, Facebook, and anything else that burns up a lot of memory will be unbearably slow.

Another distro I just thought of that no one mentioned on here that should work well is AntiX, which is an ultra-lightweight version of Mepis that is based on Debian (same parent distro that Ubuntu is based on) and features the lightweight IceWM desktop.  I've used it before and I can tell you for a fact that it's pretty snappy, although that was on a computer with 512 MB of RAM, too.  But I think it should be fairly snappy on 256 MB of RAM and will probably run acceptably on 128 MB, but will probably be a bit slow on 64 MB of RAM.

Basically, pretty much anything is going to be pathetically slow on only 64 MB of RAM.  Try to get it upgraded to at least 256 MB if you can, and that way, it'll be usable for YouTube, Facebook, and such.

Good luck and hope this helps.
Fred in St. Louis

---

### Post by Nick_Jinn on 2010-08-04
Damn Small Linux and puppy Linux are the ones I would go with. Those are the best of the most lite weight distros.


Can you up the ram? Does it take SD RAM? Make sure you get the correct type of RAM for it.

[http://www.google.com/products/catalog?hl=en&q=SDram&cid=9382502641542057366&ei=xi9aTPKNF5a4igTcy52YAg&sa=title&ved=0CAcQ8wIwADgA#p](http://www.google.com/products/catalog?hl=en&q=SDram&cid=9382502641542057366&ei=xi9aTPKNF5a4igTcy52YAg&sa=title&ved=0CAcQ8wIwADgA#p)


Upgrading the Ram could open up some doors for you. You could run Puppy Linux, which isnt so bad.

---

### Post by JBAlaska on 2010-08-05
If you want a easy setup with good HW detection, definitely try   Puppy Linux.

I've run it on puters with those specs and it works fair to good.

I would say get some more ram, but prices on the older stuff has gone out of sight.

---

### Post by claracc on 2010-08-05
I would recommend deli linux [http://polishlinux.org/choose/linux-on-old-hardware/](http://polishlinux.org/choose/linux-on-old-hardware/). I installed it one year ago in a very old pentium 133 MHz, 16 Mb ram and ¡it worked!, also I could browse with dillo. It recognized all the very very old hardware.
Also, person in charge of the distro is very kind and he can help with any problem you have to install the OS.

---

### Post by kelvin spratt on 2010-08-05
Mepis does a nice lightweight distro this is from their site. 
antiX works on computers with as little as 64 MB RAM, though 128MB  RAM is the recommended minimum and the 486 kernel version should work on  AMD K5/k6. antiX is fast and has low RAM usage running live or installed.
This should work as I used it recently with a 256mhz possessor and it worked quite well.

---

### Post by BlazeFire247 on 2010-08-05
Try Lubuntu, Damn Small Linux and Puppy Linux. Xubuntu is good too.

---

### Post by fuzetsu490 on 2010-08-05
definitely puppy linux, it would be pretty tough to run it well with only 64MB of ram but if you create a swap partition it should ok.

---

### Post by rolnics on 2010-08-05
I'd go with puppy as well, currently running it myself as my secondary main desktop, while my main rig is down for repairs!

As someone's already suggested I would try and upgrade the ram to at least 256Mb. I'm running the lastest version of puppy, and you can install packages from ubuntu, if you so wish! I'm also learning that there are a whole load of puppy derivatives out there, called puplets there is a specific pup for web browsing only. Take a look for yourself [here.]("http://www.puppylinux.org/wikka/Puplets")

---

### Post by giddyup306 on 2010-08-05
Try Fluxbuntu. I have an .iso but haven't gotten a chance to try it yet.

Min specs are 300 MHZ and 64 MB RAM, so it sounds like this is right up you alley.

[http://en.wikipedia.org/wiki/Fluxbuntu](http://en.wikipedia.org/wiki/Fluxbuntu)

In my experience, DLS tends to be buggy as hell.  Like the keyboard doesn't even work...

---

### Post by cascade9 on 2010-08-05
Celeron 466MHz, 64mb? Easy enough to get more SD-RAM, and boost the RAM up to 320MB (64MB + 256MB), or even 512MB, which is probably teh maximum for that system. 

Its not going to make the old celery into a rocketship, but it will give you far more distro options. ;)

---

### Post by Joe of loath on 2010-08-05
Upgrade the memory if you can. If you can't, a minimal install of Debian or Slackware will work pretty well, or for a more 'out of the box' solution, DSL or puppy, although puppy will be SLOW.

I'm laughing inside at all these people recommending lubuntu and xubuntu... Have you ever even tried to run these OS's on 256mb of RAM? They barely work with that much XD

---

### Post by snowpine on 2010-08-05
Giddyup, Fluxbuntu is one of those distros you really should try before recommending to others. ;) It's based on 7.10 so it's reached its "end of life"--a dead distro.

It is logical to say "the computer is old, therefore you should use an old distro, like DSL/Fluxbuntu/Ubuntu 6.06/etc" but I disagree with this logic. Using a distro that is past its "end of life" is frustrating at best, and a huge security risk at worst. Much better to use a currently active release so that you get bug fixes and security patches as well as access to a repository of up to date applications.

---

### Post by giddyup306 on 2010-08-05
> **snowpine said:**
> Giddyup, Fluxbuntu is one of those distros you really should try before recommending to others. ;) It's based on 7.10 so it's reached its "end of life"--a dead distro.

Then it should match his computer being that it seems like it's at the "end of life".  ;)

---

### Post by hunterkasy on 2010-08-05
I do want to thank everyone for their input.  I will see if my friend wants to put more money into it with purchase of some memory, I will recommend against it. but he is set in his ways.  


As for some who say that computer is totally useless, It is still good for a firewall server, by installing smoothwall on it

---

### Post by Nick_Jinn on 2010-08-06
Fluxbox is fast for power users, but with Puppy you get a nice GUI with comparable performance. Its really nice. Puppy is probably easier than fluxbox for your dad.

---

### Post by slooksterpsv on 2010-08-06
> **hunterkasy said:**
> I do want to thank everyone for their input.  I will see if my friend wants to put more money into it with purchase of some memory, I will recommend against it. but he is set in his ways.  


As for some who say that computer is totally useless, It is still good for a firewall server, by installing smoothwall on it

I was just going to post, why not make it a firewall, but you beat me to it.

Good luck!

---

### Post by soldier1st on 2010-08-06
As others have said DSL or puppy linux will do fine but what would really help is adding more memory.

---

### Post by K.Mandla on 2010-08-06
> **hunterkasy said:**
> I have a old compaq Celeron 466mrz with 64mb of memory,  I know it is really old, but I have this friend who is 50, he is determined to get it up and going again, you know because back in the day it was the fastest on the market, I have been unable to explain that the good old times are a little different from today, SO I am wondering what Linux distro would be the best for that slow of a machine?
Arch Linux.

---

### Post by Nick_Jinn on 2010-08-06
> **K.Mandla said:**
> Arch Linux.


Are you sure Arch-Linux is a good idea for someone who apparently doesnt know a whole lot about computers since the days of MS Dos amd windows 98? Puppy seems easier, though installing packages isnt as smooth as on a cutting edge OS. Actually using it provides a pretty nice experience and is fairly user friendly.

---

