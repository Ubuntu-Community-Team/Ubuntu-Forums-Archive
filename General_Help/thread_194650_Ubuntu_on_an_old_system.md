---
title: "Ubuntu on an old system"
date: 2006-06-11
forum: General Help
---

### Post by catflea on 2006-06-11
Hi,

Is there any chance that I am likely to be able to get ubuntu running on an oooold system?   Investigation sugessts its a Pentium 233 mmx with a whole 32mb Ram and a 3gb HDD.

I just want a simple PC that I can keep in my Garage to use the Net out there, play music on an run a database on where I've put different parts of my restoration projects.

If not ubuntu, any suggestions for another distro would be grand (although I think I will need to get wireless support sorted)

---

### Post by ddumanis on 2006-06-11
Puppy Linux, Damn Small Linux, and Vector Linux all have good reputations for running on dinosaur hardware.

I have a 500 MHz laptop and it's running Dapper fine, but that's probably the bottom I would try it on.

---

### Post by glotz on 2006-06-11
I think all Ubuntu variants require a minimum of 64 megs ram since the server (= no graphical desktop environment at all) seems to require that. [http://help.ubuntu.com/6.06/ubuntu/serverguide/C/preparing-to-install.html](http://help.ubuntu.com/6.06/ubuntu/serverguide/C/preparing-to-install.html)

(ddumanis, I'm sure Xubuntu Dapper would run on pretty low end machines.)

---

### Post by grsing on 2006-06-11
If you could find out what type of RAM it takes and if there are any extra slots, you could probably find more on ebay for cheap.  That's the biggest problem I see with it; trying to run an internet browser with 32MB of RAM would be painful, regardless of whether Ubuntu (or any other distro) would run (it might work with Lynx, a text-only browser, but I don't have any experience with it).

---

### Post by dicecca112 on 2006-06-11
yeah running dapper on a PIII 1ghz 512mb of ram, and its too slow for my tastes but this is going from a Dual Core 820D with 1GB of ram.  So, I personally think it would crawl on a system like that

---

### Post by adssse on 2006-06-11
As someone stated earlier, Damn Small Linux will probably be your best bet if you need a gui. They have a very nice project over there that runs great on old hardware. I ran it for quite a while on my old 233mhz with 128mb ram.

---

### Post by skelooth on 2006-06-11
There's just not enough ram, you're going to have to stick a dimm in there to make it at least 128mb if you expect to use that computer in any half way modern way.

Once you do that it'd probably run xubuntu fine. I just installed xubuntu on a 500mhz machine and it runs faster than it's original windows 95.

---

### Post by Kratos on 2006-06-12
Hate to hijack this thread, but I have my own system I'm trying to put together.

200MHz Pentium Pro
128MB RAM

It runs Xubuntu fine, but I want to know if it could handle Edubuntu, as I plan to give it to my little brother and sister (they enter 6th grade this fall). 

Thanks in advance.

Kratos

---

### Post by glotz on 2006-06-12
Looks like Edubuntu uses GNOME. (why the *fsck* can't it read clearly on their homepage??) GNOME can be very very sluggish on that box. I bet it's a nogo. However, you can probably install most of the programs on Xubuntu too...

(I might be totally wrong but Edubuntu is only so much hot air to me...)

---

### Post by kevlarman on 2006-06-12
I'm running dapper on a pentium 3 500mhz (256 ram) and it runs just fine (in fact I was surprised at the lack of bloat in gnome after comming from fedora). Xubuntu should run just fine on a pentium 233, but like others have said running a browser on that little memory isn't the greatest idea (ram is cheap, get some more and you should be fine). 

kratos, i would recommend just installing the package edubuntu-desktop, and just see if it works (my guess would be that it would take forever to start, and it will probably be a little sluggish, but usable), otherwise you can access all the apps from xfce, which will be almost the same thing.

---

### Post by catflea on 2006-06-12
[QUOTE=grsing]If you could find out what type of RAM it takes and if there are any extra slots, you could probably find more on ebay for cheap.  [/QUOTE]
Theres no extra slots which is a shame!  Don't think I would be possible to get it up to 128mb

I suspect is has 2 8mb and 1 16mb ram boards.  No idea which type though - too dinosaurish for me to be able to cast back my memory

---

### Post by grsing on 2006-06-12
Wow, that really is a dinosaur.  But Damn Small Linux does say it can run on a 486 with 16MB of RAM, so it should run.  Will you get a browser working?  Probably not.  Sorry, that box may just be too old to do what you want it to do.  You could probably buy a used PC for $50 or so that would do all that just fine, if you're set on it.

---

### Post by painkiler on 2006-06-12
I am running Ubuntu Dapper on a p2 300mhz with 128mb of ram. It is very slugish, and if you treat it to fast, it will kill the xserver. I really don't enjoy using the box, but its just an old pc...

---

### Post by catflea on 2006-06-12
Maybe I should just keep win 98 on it then.   Sounds like waaay too much hassle.

---

### Post by Chickenmonger on 2006-06-12
I've got Xubuntu Dapper installed on a 300 Mhz AMD with 96 MB of RAM, and while it's usable, I'm not certain how useful it can be other than word processing, and console work.

---

### Post by IYY on 2006-06-12
It's not a hassle, just try PuppyLinux or Damn Small Linux instead of Ubuntu. It's not that Ubuntu itself won't be able to run: if you use IceWM or Fluxbox as the window manager it will even be quite fast. The problem is with the applications that come with it. Most of them are designed for a newer system, so you'll end up replacing most of them. That's why it's better to use a distribution aimed at PCs like yours.

---

### Post by glotz on 2006-06-12
DSL comes with [Dillo](http://www.dillo.org/). That's a very light graphical web browser.

And then there naturally are the text based even lighter [Links](http://artax.karlin.mff.cuni.cz/~mikulas/links/) and [Lynx](http://lynx.browser.org/).

---

