---
title: "A few minor issues on transitioning to 9.10"
date: 2009-10-30
forum: General Help
---

### Post by dwasifar on 2009-10-30
I installed 9.10 clean on a backup machine and played with it to configure it the way I like.  A few notes on the process:

**1) Some weirdness with the shutdown splash**.  Apparently the Karmic usplash theme is just a plain white Ubuntu logo at startup, and nothing at all in shutdown.  (This is separate from xsplash, which - if I understand things correctly - handles the ethereal turd-colored throbber screen that precedes the actual desktop.)  So on shutdown I get white-on-black tty messages at the upper left.  I've found some advice on disabling xsplash, which I'll probably try because I don't find the white glowing logo on the turdy background all that appealing.  If anyone knows how I can get the old Jaunty version of the Ubuntu usplash theme installed into Karmic, I'd be obliged.  But at the moment this issue is unresolved.

**2) I've lost my Grip.**  (My friends will gladly confirm this.)  I've relied on Grip and lame for CD ripping since oh, I think Dapper.  Now it's gone, and from what I've seen it is no longer being maintained.  So I switched to RipperX.  I blogged about why I chose that, and how I tweaked the configuration outside of the options it offers, so I won't repeat it here; if you're interested, [here's the link]("http://www.dwasifar.com/?p=836").

**3) Installing the kubuntu-desktop package over a regular Ubuntu installation causes problems that did not happen in earlier versions.**  I run Gnome, but I use several KDE apps (Amarok, K3B, Kaffeine, Kid3, and KTorrent, to name a few).  KDE apps don't follow Gnome settings for fonts and subpixel hinting; you need to set those up with the KDE systemsettings app.  When Kubuntu went to KDE4 (with Hardy, wasn't it?) you couldn't install KDE systemsettings independently any more.  So, since Intrepid, I'd fallen into the lazy habit of just installing kubuntu-desktop; it gave me all the KDE apps and the settings tools too.  *This no longer works.*  If you do it, a lot of stuff in Gnome's Appearance tool no longer has any effect.  So I started over and found that installing kdebase-workspace gives me fully functional KDE systemsettings without installing all of kubuntu-desktop.  Then I just install the desired KDE apps individually.  This probably would have worked fine in Jaunty and Intrepid too, I just never needed to figure it out before.

Other than that, no show stoppers.  Most other things work as expected, or nearly so.  The system boots in 24 seconds (take THAT, Windows 7!).  Generally I think this is going to be a pretty positive experience.

---

### Post by CthulhuFan on 2009-10-31
> **dwasifar said:**
> 

**2) I've lost my Grip.**  (My friends will gladly confirm this.)  I've relied on Grip and lame for CD ripping since oh, I think Dapper.  Now it's gone, and from what I've seen it is no longer being maintained.  So I switched to RipperX.  I blogged about why I chose that, and how I tweaked the configuration outside of the options it offers, so I won't repeat it here; if you're interested, [here's the link]("http://www.dwasifar.com/?p=836").



Same here, grip is very near and dear to me as well.  I notice that it's not on the current debian package listing either.  :(

In the mean time, I'll check out that RipperX thanks for posting that.

---

