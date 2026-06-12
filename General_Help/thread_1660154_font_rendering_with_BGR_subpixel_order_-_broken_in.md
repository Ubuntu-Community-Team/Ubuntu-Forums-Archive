---
title: "font rendering with BGR subpixel order - broken in Maverick?"
date: 2011-01-05
forum: General Help
---

### Post by Quicksand on 2011-01-05
This has me stumped.  But you might be able to help me . . .

I have one of the few B-G-R-patterned LCD panels out there, a Dell 1800FP.  In past versions of Ubuntu, I have been able to adjust the font settings in the Appearance pref panel to set the "BGR" subpixel order, rather than the default "RGB" order, and I'd get excellent font rendering.  This doesn't seem to work any more in Maverick, for the most part.

In fact, if I have the detailed font rendering settings (System->Preferences->Appearance->Fonts->Details) up on screen, it doesn't seem to do ANYTHING AT ALL when I click back and forth between "RGB" and "BGR."  No matter how closely I look, not a single pixel changes.  I can see small changes (as expected) when I go back and forth between "RGB" and "VRGB," for example, but "RGB"<->"BGR" appears to do absolutely nothing.

My fonts are blurry, fringy, and ugly in all of the Gnome/GTK applications I have.  It appears to be using the incorrect "RGB" subpixel order regardless of what I select in the preference panel.  (If I take a screenshot and mirror-image it, fonts look very good in the backwards image -- this confirms that it IS in fact the incorrect RGB subpixel order I am seeing ordinarily).

But in Firefox, for some reason, the RGB/BGR setting _does_ work.  If I select "BGR" in the preferences and refresh a web page, it looks GREAT!  Re-select "RGB," refresh, and it's ugly again.

So there's something weird going on.  This setting isn't being respected by my desktop or most Gnome/GTK applications I use.

I have confirmed this is NOT a personal setup issue, as I can reproduce it fully when booting from the Maverick desktop installation LiveCD.  I think something is broken.

Before I report this as a bug in Launchpad, I'd like to have some confirmation that others are seeing the same phenomenon.  Even if you have an R-G-B monitor like 99% of them out there, you can check by toggling back and forth between RGB and BGR and looking at your Gnome Panel, icon text on the desktop, text in a Terminal, or whatever.  In my case, none of those things seem to respond correctly.

I'd appreciate some assistance on this -- thanks!

---

### Post by Quicksand on 2011-01-07
Anyone?

Am I the only one with a BGR monitor around here?  :confused:

I tried running a bunch of virtual machines (just downloaded the desktop installation ISOs and "booted" them via kvm).  Here are the results:

Ubuntu 10.10: BROKEN - no BGR font rendering

Xubuntu 10.10: BROKEN - no BGR font rendering

Ubuntu 11.04 alpha: BROKEN - no BGR font rendering

Ubuntu 10.04.1: WORKS FINE!

There's a bug somewhere, but I don't have the slightest idea what package to report it against so it gets the right attention.

---

### Post by Quicksand on 2011-01-11
Last bump before I take it to Launchpad.

All of the above VM images were the 64-bit versions, and just for the sake of completeness, I decided to also try Ubuntu 10.10 32-bit.  BROKEN.  No surprise.

---

### Post by velmont on 2011-07-17
Please link to your bug so I can me-too it. ;-)

Strange how well that worked in Firefox. Didn't know I had to refresh though, but now that I did, it's beautiful ;-)

---

