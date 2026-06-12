---
title: "Best driver for HD4200?"
date: 2009-12-07
forum: General Help
---

### Post by wotsit on 2009-12-07
Sorry if I'm sounding a bit thick!

I've been warned against the fglrx driver, but without much to back up the argument. Is this driver really bad? I have noticed that there is a new release as of 17/11/2009?

Is this the same as the driver found on amd's website? (ATI Catalyst™ 9.11 Proprietary Linux x86 Display Driver)

I've heard in forums (can't name which ones, just while i was browsing) posts which say "Oh don't use that driver, use this one and compile it (link) it was made by xyz some weeks ago as an alternative" but I can't really find any others out there?

---

### Post by coffeecat on 2009-12-07
I have the ATI Radeon HD 4200 graphics in my Acer laptop and I can tell you that 10-14 days ago, when I tried it, the proprietary fglrx driver in Karmic was really, really, **really** bad news. I'm using the open-source radeon driver and everything's fine except that I can't enable compiz.

I believe that if you install the 2.6.32 kernel, a development version of the xserver and a development version of the ATI radeon driver, you'll be able to enable compiz, bur for myself, I'm going to wait.

I'm going to wait for either ATI to release a usable driver for this card, or for Lucid and hope that the open-source stuff supports compiz then.

---

### Post by wotsit on 2009-12-08
Ok thanks for the tip, I guess i'll have to wait. Why is fglrx so bad for the HD4200? Crashes? System hog?

Also Im going to install kubuntu, this uses the KWin manager right?

Im a bit confused as to compiz's 'role' in kubuntu, is it basically the same as ubuntu where I need to enable it for advanced desktop effects?

I would have thought that amd would have made its driver at least workable since the HD4200 has a) been out for a while and b) is in loads of integrated mobo's for laptops and desktops...

---

### Post by coffeecat on 2009-12-08
> **wotsit said:**
> Why is fglrx so bad for the HD4200? Crashes? System hog?

Every time I tried to move a window, it tore and lagged horribly.

> **wotsit said:**
> Also Im going to install kubuntu, this uses the KWin manager right?

Im a bit confused as to compiz's 'role' in kubuntu, is it basically the same as ubuntu where I need to enable it for advanced desktop effects?

Sorry - I've never really used KDE 4 except for a few brief try-outs. I believe it uses its own compositing manager, so you can enable some 3d effects through whatever the KDE configuration utility is called.

> **wotsit said:**
>  I would have thought that amd would have made its driver at least workable since the HD4200 has a) been out for a while and b) is in loads of integrated mobo's for laptops and desktops...

Agreed! :(

But give it a try yourself and see if you have better luck. I had great difficulty actually enabling the driver. The hardware drivers utility showed the driver but nothing happened when I clicked on activate. I think eventually I used Envy. Perhaps something went wrong on my system, so if you do try it and it works OK, please post back.

But if you get what I got and you want the open-source radeon driver back, you simply uninstall all the fglrx stuff, delete (or rename) xorg.conf and reboot.

---

### Post by jaxxed on 2009-12-16
I think the 4200 is an R600 chip card.

If so then know that the release version of the radeon driver doesn't completely support compositing effects, and therefore will likely not support compiz (it doesn't support the kde compositing effects yet.)
I'm using karmic, and I use the [ppa: xorg-edgers]("https://launchpad.net/~xorg-edgers") radeon driver with an R700 chip (HD4600 modibility 1gb,) upgraded the kernel to [mainline]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") 2.6.32 driver - which was all easy to do using a ppa for the drivers and 3 .deb installs for the kernel, and they worked beautifully.  I think I might have had some issues with power management, but nothing drastic.

I recommend the newer radeon drivers if you want any blign.  Go for it and lose the last of your few blob/closed drivers.

Yesteday I upgraded my kde to the 4.4 beta and lost my compositing, but I'm not sure it it's a radeon/dri2 issue, a kernel issue, or just 4,4 yet.

---

### Post by kronictokr on 2009-12-26
ive just enabled the driver through system>>administration>>hardware drivers
gives me ati catalyst control center

followed by adding this

Gnome menu | System | Preferences | Main Menu | Applications | Other | ATI Catalyst Control Center (super-user)" | Properties | Command:
Change "amdxdg-su -c amdcccle" to "gksu amdcccle"

found on this post
[http://ubuntuforums.org/showthread.php?p=8563528#post8563528](http://ubuntuforums.org/showthread.php?p=8563528#post8563528)

i have dual monitor laptop/lcdtv its working great so far

edit: have not tried 3d compiz yet , but im about to. pls msg me if you have done so successfully with this graphics card

---

### Post by coffeecat on 2009-12-27
> **jaxxed said:**
> I think the 4200 is an R600 chip card.

According to [Wikipedia](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units) the HD4200 is based on the RV620. 

> **kronictokr said:**
> ive just enabled the driver through system>>administration>>hardware drivers
gives me ati catalyst control center

followed by adding this

Gnome menu | System | Preferences | Main Menu | Applications | Other | ATI Catalyst Control Center (super-user)" | Properties | Command:
Change "amdxdg-su -c amdcccle" to "gksu amdcccle"

Do you have a Radeon HD4200 like the OP and myself or another ATI card? I've just tried re-enabling the fglrx driver and running Catalyst Control Centre with your posted fix. CCC certainly does run with 'gksu amdcccle' but it makes no difference. The fglrx driver with this HD 4200 card on my system is a complete and unmitigated disaster.

I'm going to look at the PPA edgers packages when I have a chance

---

### Post by kronictokr on 2009-12-27
yes sir , my graphics card is a ati radeon HD 4200 mobile. 64bit karmic.
i uninstalled and reinstalled this morning works great, you do have to do the fix for the admin comand code, and then configure your settings. but ive got 2 workspaces on 1 desktop, 1 laptop and 1 720p lcd. ive been working on my laptop and watching movies on my tv flawlessly.
compiz works great as well. all in all , im one happy camper.
just wish i could find a replacement for "hotspot shield" slows the cpu down , but i only use it to watch hulu in canada.

---

### Post by coffeecat on 2009-12-27
Curious, isn't it, how the 'your mileage may vary' principle can operate even with apparently identical hardware. I've seen threads from people who can't get a wireless chipset working properly that works just fine in my laptop. Now the shoe is on the other foot with a graphics card. All very strange.

Thanks for confirming that, though.

---

### Post by kronictokr on 2009-12-28
well ive also got compiz working on it, i plan on loading a demo video on youtube in the next day or so , ill show my laptop and all , so you can see it with your own eyes. just about time to sleep , so most likely the morning. ill also check my history and booksmarks to see if ive done something extra.  might have used a ati config comand in terminal.
i have a mark backup if you'd like to check it out.

---

### Post by Nburnes on 2009-12-28
The HD 4200 works just fine in my Karmic? Even with Compiz installed I haven't had any tearing or stutters.

---

### Post by n3had on 2009-12-30
people who have been trying opensource drivers for HD4200. Are you guys using ati/radeon or radeonhd from the ppa?

---

### Post by kronictokr on 2009-12-30
Im using the HD version see this thread for for info
[http://ubuntuforums.org/showthread.php?t=1350637&highlight=ati+radeon+4200+HD](http://ubuntuforums.org/showthread.php?t=1350637&highlight=ati+radeon+4200+HD)

---

