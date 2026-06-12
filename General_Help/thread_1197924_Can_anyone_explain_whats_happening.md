---
title: "Can anyone explain whats happening?"
date: 2009-06-26
forum: General Help
---

### Post by oxf on 2009-06-26
[SIZE=3]This little problem, if thats what it is, started today. Its seems to be associated with the scrolling function on the touchpad on my laptop. Maybe associated with other function too but cant tell.

I have Firefox open and am moving around a web page scrolling up and down with the touchpad. Briefly the scrolling freezes, the fan on the processor kicks in full power and at the same time the display colour fades to black/white. I wait a second or two and the colour comes back as the fan powers down. Then the scrolling is working again.

Someone please tell me whats happening and why?
 [/SIZE]

---

### Post by Yvan300 on 2009-06-26
I have no clue at all, maybe ubuntu has wrongly recognized some of your hardware

---

### Post by Polaris96 on 2009-06-26
try installing another browser.  Iceweasel, maybe, since its almost the same thing.  See if it's still happening.  If it's not then:

sudo apt-get purge firefox
sudo apt-get install firefox

If it does the same thing ... that's above my paygrade, sorry.

---

### Post by earthpigg on 2009-06-26
ill mirror what others said: uninstall firefox (completely, using **_purge_** and not remove) and reinstall...

also, you could try some different browsers: opera, chrome beta, iceweasel to see if its firefox's problem or something different.

---

### Post by oxf on 2009-06-26
Yes I'll try those sugestions if it seems like it's a persistent problem. I'd never encountered it before today on either Hardy or Now Jaunty. In my mind when this happens something is taxing the resources of the processor which causes it to freeze/run overtime and thus the fan kicks in. Of course I could be wrong with all this. 

It happen again a few minutes ago. This time I knew it was coming because the fan started up first, and then sure enough display faded to black/white and while I sat back and took a sip of my coffee it came back to colour and the fan powered down. 

  I'll try the firefox option first if this persists. None the less its a strange one!

BTW my laptop is an Acer Aspire M2000 with AMD Athlon 66 processor, 
Display adaptor ATI Radeon Xpress 200M, 32MB shared memory
 and 1GB RAM

---

### Post by philcamlin on 2009-06-26
non compatible hardware ??:confused:

try opera?

---

### Post by Ayuthia on 2009-06-26
Are you using the 64-bit version of Ubuntu?  If so, how did you install flash?

It could be that Firefox is using flash and something was a little odd.  It used to happen a lot with nspluginwrapper and flash (fan starting up).  I have not had it happen lately since switching over to the 64-bit flash alpha.

Also, you mention things going to black and white.  Are you using compiz?  You might turn it off and see if things get better.

---

### Post by oxf on 2009-06-26
> **Ayuthia said:**
> Are you using the 64-bit version of Ubuntu?  If so, how did you install flash?

It could be that Firefox is using flash and something was a little odd.  It used to happen a lot with nspluginwrapper and flash (fan starting up).  I have not had it happen lately since switching over to the 64-bit flash alpha.

Also, you mention things going to black and white.  Are you using compiz?  You might turn it off and see if things get better.

No I'm using Jaunty 9.04 32bit and yes I did install Adobe flash when prompted to.
I'm not aware I'm using compiz but where do I turn it off from?
thanks

---

### Post by AoSteve on 2009-06-26
That's firefox lagging out.  It does it to me with certain themes and the like installed.  You should see it in Vista when someone who loves themes has it modded out LOL!   My cousins laptop will go into black and white mode for about 2 minutes sometimes!  

Do like was said before though, purge, not remove, firefox and reinstall.  It should fix you right up!

> **oxf said:**
> \
It happen again a few minutes ago. This time I knew it was coming because the fan started up first, and then sure enough display faded to black/white and while I sat back and took a sip of my coffee it came back to colour and the fan powered down. 


That's because it's going to 100% cpu usage by the way.  :)

---

### Post by oxf on 2009-06-26
> **AoSteve said:**
> That's firefox lagging out.  It does it to me with certain themes and the like installed.  You should see it in Vista when someone who loves themes has it modded out LOL!   My cousins laptop will go into black and white mode for about 2 minutes sometimes!  

Do like was said before though, purge, not remove, firefox and reinstall.  It should fix you right up!

OK purge, point taken. Any benefit  for just doing a fresh install?

---

### Post by Ayuthia on 2009-06-26
> **oxf said:**
> No I'm using Jaunty 9.04 32bit and yes I did install Adobe flash when prompted to.
I'm not aware I'm using compiz but where do I turn it off from?
thanks

If you don't recall installing it, you are most likely not using it.  You might check and see if Desktop Effects is running.  I want to say it is in System->Preferences->Appearance, but I could be wrong.  I am currently in KDE and I can't remember the exact location.

---

### Post by AoSteve on 2009-06-26
To check for compiz in gnome, simply right click the desktop and select "Change Desktop Background"  and check the "Visual Effects" tab.  If it's on anything above "None" then compiz is running.  I highly doubt compiz is causing any problem though.

And a fresh install pretty much is the best thing for firefox.  I've noticed plenty of problems with firefox across different platform.  Usually reinstalling is a good fix after a purge.  I think it's more or less that firefox can't manage a LOT of addons and the like real well.  Plus, when certain things are enabled or not completely compatible, it causes these slowdowns.  I've even seen a theme cause it to do this for minutes on my E8400 powered machine, even with 4GB of ram.   

Like I said, try a purge/reinstall and see how that works.  Sometimes it can just be the cache of the browser causing problems.  I've noticed that Firefox doesn't do the best job at purging it's own cache either.

---

### Post by oxf on 2009-06-29
Well I've sort of resolved it or more accurately lets say gotten to the bottom of it the problem and seems like its not me! I'm including this just FYI for anyone out there.

I tried reinstalling Firefox and then did a complete clean install of Ubuntu. No change the problem occasionally happened. Then it occurred to me that this was ONLY happening on one website. I investigated further.

The website concerned is a social networking site that my partner sometimes uses. Included in the website is a option for a music player that is not actually on the site itself. i.e. you go to the external playlist site, create your playlist and get a code that you can use back on the network site to link it the playlist site. Then your music plays on you page...or used to. 

I noticed that Firefox froze and did its thing when it was trying to load the playlist. I went to the external playlist site looked arround and it seems lots of people are have similar problem with Internet Explorer completely crashing when on networks site that use this music playlist. So its nice to know its not me. We just disabled the music playlist on the external site so  it does not link any more and everything is just fine.

Just FYI..

---

