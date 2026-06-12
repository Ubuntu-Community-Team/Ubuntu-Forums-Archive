---
title: "Glitchy Intel HD graphics on Ubuntu 11.10"
date: 2011-10-16
forum: General Help
---

### Post by substanceD on 2011-10-16
Hello, after upgrading to Ubuntu 11.10 from 11.04, my laptop's graphics drivers seem very glitchy, with the mouse disappearing or flickering when I mouse over or click on a variety of things, and menu text disappears or shows graphical artifacts occasionally. Transparency also has stopped working, although this is less of an issue to me.

Something that has been causing me a lot of trouble is the fact that I have ATI switchable graphics; I have an HP dv6-6190us, which has both an ATI 6770M and an integrated Intel HD 3000. I don't care about using the dedicated card while on Ubuntu, and I have it disabled currently:

```

$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```

I'm sure that my graphics configuration is in some sort of a weird state, because I installed/uninstalled AMD's Catalyst software multiple times through a variety of methods trying to get Ubuntu to handle switchable graphics correctly before giving up on that. Like I said, though, Intel HD graphics were working fine on their own before the upgrade. Is there a way I can make sure that I have the right drivers in use for the integrated Intel HD graphics and/or switch to some that are less buggy? It's possible that starting over from scratch with my graphics drivers and x-server configuration would fix things, so I would be happy to try that if anyone has suggestions.

Thanks!

---

### Post by Antarell on 2011-10-16
I found when I was mucking with the ATI drivers on my DV6-6023tx that it would muck up GLX when I uninstalled FGLRX. I used Synaptics to re-install "libgl1-mesa-glx" and that seemed to sort it out. You could try to re-install "xserver-xorg-video-intel" as well (and remove any flgrx stuff while you are there). To re-install you right click on the installed item and "mark for re-installation". You could also use "sudo apt-get install --reinstall packagename" on the console.

For more power savings have a look [here]("http://bit.ly/omzzHD") as well :-). Sort your existing graphics problems out first though, as the extra power savings are based on the Intel Graphics chip/screen. They work fine on another DV6-61xx that I know off.

edit: The new Catalyst drivers now work with the DV6's!! See my post below!

---

### Post by substanceD on 2011-10-17
Well, I tried reinstalling the packages that you suggested as well as some others but I did not make any progress. I'm just going to do a fresh install of 11.10 and avoid installing the fglrx drivers this time. Thanks for trying to help.

---

### Post by Antarell on 2011-10-17
> **substanceD said:**
> Well, I tried reinstalling the packages that you suggested as well as some others but I did not make any progress. I'm just going to do a fresh install of 11.10 and avoid installing the fglrx drivers this time. Thanks for trying to help.

No problems, it's strange as but that worked for me twice :confused:

I apt-get purged fglrx* then reinstalled mesa glx. There must be something else going on as well.

[edit: The Radeon now works! ]("http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html")

---

