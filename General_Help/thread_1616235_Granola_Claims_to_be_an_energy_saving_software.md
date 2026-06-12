---
title: "Granola: Claims to be an energy saving software"
date: 2010-11-08
forum: General Help
---

### Post by paparozoumis on 2010-11-08
Available for Linux, too
[http://grano.la/](http://grano.la/)

Anyone already tried it or knows anything about it?
Looks promising 
I will report my findings

---

### Post by supergrav on 2010-11-08
Already tried it about two months ago...I'm not really satisfied because it slows down things. I always have to switch between different modes to get full power or economy.

---

### Post by paparozoumis on 2010-11-08
> **supergrav said:**
> Already tried it about two months ago...I'm not really satisfied because it slows down things. I always have to switch between different modes to get full power or economy.

I have already installed it on two Windows machines (one laptop and one desktop). 
On the desktop I have connected an electricity consuming gauge that shows the power that the device draws at any given time but I need more time to test it, as the program is being installed just  a few hours ago. 

I haven't noticed any delay on the machines' responses yet.
Ubuntu installation to come shortly

---

### Post by supasoaker on 2010-12-04
I have it on a windows machine with a power display device, yes it does save watts, my machine is a dual core AMD 6000+ 4GB ram and onboard video card 256MB - with ASUS Cool and Quiet enabled plus Granola my consumption can go down to around 48 watts running winxp.

I think windows vista is supposed to consume only 3 watts after a long idle...............don't know much about win7.

Linux has always consumed less power by at least 20 watts usually :)

If you watch the video on their website you can see how the computer reacts - it looks like you will experience a very slight delay at the beginning which will be Granola calculating the demand, after that performance should be the same. Yes, Granola will consume resources and be least efficient when at high load  but is very good for idle.

Anyone know anything specific about the type of algorithms that Granola uses to save this energy?

---

### Post by paparozoumis on 2010-12-04
Well, since you brought it up again.. 

I have some measuring results and I can say it is not as sufficient as it claims to be. 
I have connected a wattage measuring device on my computer (desktop) and it doesn't make any difference when Granola is on or off. 
The consumption is very similar and in NO WAY there is a 20% less consuming when Granola is ON, as it claims. 

I have Granola running on three machines of mine (the other two being laptops) with the desktop being 24/7 on but since I haven't noticed any delay on reaction I will keep it there ....

Overall, it doesn't do any good but it doesn't harm anything either...

---

### Post by paparozoumis on 2010-12-04
> **supasoaker said:**
> I have it on a windows machine with a power display device, yes it does save watts, my machine is a dual core AMD 6000+ 4GB ram and onboard video card 256MB - with ASUS Cool and Quiet enabled plus Granola my consumption can go down **_to around 48 watts running winxp_**.

I think windows vista is supposed to consume _[U]only 3 watts _[/U]after a long idle...............don't know much about win7.

Linux has always consumed less power by at least 20 watts usually :)




How did you actually measure these figures?

I have this thingy connected 
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=280551305920](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=280551305920)
and it has NEVER gone below 100Watts even with the monitor switched off. 
I always keep my hard disks on because I seed torrents etc and I never hibernate or suspend and under these conditions consumption is always above 100Watts with maximum load around 150Watts (when I render DVDs etc) on an XP machine.

Figures are almost identical no matter if Granola is or or off.  

I haven't measured it running Ubuntu as a live disk won't give me a real indication of power consuming.

---

### Post by dcstar on 2010-12-04
> **supasoaker said:**
> 
...........
Anyone know anything specific about the type of algorithms that Granola uses to save this energy?

As it says on the website, it uses "dynamic voltage and frequency scaling" which has been built into the Linux kernel for years now and is activated by default.

This product should be targeted at old operating systems that never fully supported this sort of feature which is now available in modern hardware - old operating systems like Windows XP.

This product is probably a total waste of time for Linux, Linux already has these capabilities and the tools for users to make any power savings as aggressive as they like.

---

### Post by gulmer on 2011-02-01
I just installed granola on 2 machines,1 run 10.04 is a Pentium 4,the other is an AMD 64 dual core. The GUI on the AMD doesn't come up on the desktop.Anybody have an opinion on how to get it working?

---

### Post by paparozoumis on 2011-02-02
> **gulmer said:**
> I just installed granola on 2 machines,1 run 10.04 is a Pentium 4,the other is an AMD 64 dual core. The GUI on the AMD doesn't come up on the desktop.Anybody have an opinion on how to get it working?

Did you try to reinstall it? Perhaps something went wrong during installation?
Other than that, I can't think of anything else....

---

### Post by blazemore on 2011-02-02
It's total bull. I have an energy monitor sat next to my desk, and there's no noticeable difference (to the nearest 5W).

There is, however, a noticeable slowdown. Just let the kernel, and your CPU itsself, take care of controlling the clock speeds.

---

### Post by paparozoumis on 2011-02-06
Eventually, granola found its way to the bin..
I realized that it messed up the energy profiles on the windows machine and it wouldn't allow it to enter in energy saving modes. 
It wouldn't  allow it to run screen savers (random behavior) and it never allow it to stop the hard disks when they were not in use. 

Well, since it didn't offer much of result, I finally removed it off of  all the machines, including the Ubuntu ones. 
Bye bye Granola :)

---

### Post by monkeypigs on 2011-12-20
Thanks for this thread, (Yes I know it's quite old now) 

I've installed Granola on my Ubuntu laptop, and it merrily reported away how much energy I was saving (naff all)

Thought I'd give it a shot on my Ubuntu (oneric) server...... service simply does not start, so I e-mailed them, *eventually* got a reply that my box doesn't support it as it doesn't have Intel SpeedStep or it isn't enabled..... so tough luck! It's odd that the BIOS says that it is enabled and the ondemand govenor does a great job of ramping the fans up when it needs to (eg transcoding using subsonic)

I like the idea of Granola, but their support is non-existent and their product does not work (eg it simply fails with no trace why - even with verbose or debug logging enabled) and also, as highlighted earlier, does not work (energy meters report no saving over the ondemand cpu scaling)

Duly removed from my laptop, and let this be a tale of caution to anyone else that stumbles across this thread trying to get either the CLI version or the GUI version running, pretty graphs on websites aren't always what they seem!

---

