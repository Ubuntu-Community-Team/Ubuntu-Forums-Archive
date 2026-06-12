---
title: "Where is XFree86?"
date: 2006-02-13
forum: General Help
---

### Post by Sirin on 2006-02-13
Where is XFree86? X.org has too many bugs when it comes to Intel videocards and it messes up when I try to play Enemy Territory. When I was using Fedora Core 1 (Which had XFree86, by the way), I could play Enemy Territory very fluidly with no configuration whatsoever. In Hoary, I had to tweak lots of things JUST to get the damn display to work. I tried to play ET last time in Breezy, and it just MESSED up my X.Org configuration. I had to reinstall Ubuntu all over again. Now I know that this may not sound like anything dense compared to hearing "reinstall windows", but it is dense. I had to configure X.Org ALL OVER AGAIN!! I lost all of my files because of this X.Org error. I just couldn't take it anymore. X.Org SUCKS for Intel Integrated Users. Where can I get XFree86? I can't take X.Org!!! :evil:

---

### Post by Lord Illidan on 2006-02-13
Calm down. What is the make and model of your Intel Video Card? Maybe someone found a way of making it work under Ubuntu?

---

### Post by Sirin on 2006-02-13
[QUOTE=Lord Illidan]Calm down. What is the make and model of your Intel Video Card? Maybe someone found a way of making it work under Ubuntu?[/QUOTE]

Intel® 82865G. This card runs very fluidly on an XFree86 System.

---

### Post by Sirin on 2006-02-14
Anybody find a way?

---

### Post by Garyu on 2006-02-14
[QUOTE=Sirin]Anybody find a way?[/QUOTE]

Did you see this post:
[http://www.ubuntuforums.org/showthread.php?t=46524&goto=nextoldest](http://www.ubuntuforums.org/showthread.php?t=46524&goto=nextoldest)

According to Intel:
[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)
They seem to think that XFree86 is the right way to go with this card. I'm not the one to ask how to switch X server, but I'm sure it is possible if you try hard enough, even with Ubuntu. The community support is probably limited though... :-k

---

### Post by Sirin on 2006-02-16
> According to Intel:
[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)
They seem to think that XFree86 is the right way to go with this card. I'm not the one to ask how to switch X server, but I'm sure it is possible if you try hard enough, even with Ubuntu. The community support is probably limited though... :-k

Hmm. But it may ruin my system. :-?

I wwonder why we don't run XFree86 in the first place? That seems to have better graphics support.

---

### Post by LordBug on 2006-02-16
XFree86 did a licensing change that nobody agreed with.  XFree86 stuck with it, so everyone changed to X.Org.  X.Org, FYI, is a fork of the last version of XFree86 before the license change.

If you seriously want to setup XFree86 to replace X.Org, you're likely on your own.

---

### Post by pravuil on 2006-08-22
That's bull but I guess that's the way it goes. The problem I'm having revolves around limits imposed by xorg. Xorg doesn't support framebuffers at all when it comes to proprietary graphics drivers. I know people always question why people need bootscreens or the like, they end up suggesting the default installation. Number one, it's to produce industry presence to provide a greater feel of professionalism. You can edit the usplash screen but I've done it and usplash is beyond buggy. Too much garbage and the resolution restriction is abhorrent. I design graphics on a daily basis for my business and if I can't have presence and graphics acceleration, I look like an idiot. I lean on Microsoft for the majority of my duties and I've tested Redhat, Suse, Debian, Mandrake(Mandriva) working on Gentoo and Arch at the moment to find a better alternative. The problem with this is if I were to use Canonical support for $250+ up to 1200+. I'm limited to the options already available within the community support version. If I were to deviate I would break TOS and invalidate my support. I wouldn't mind paying for support if I was guaranteed reliability and basic expectations for presentation. Xorg isn't too terribly buggy when using x-window-system-core with xdm and fluxbox (which works better than any other window manager I've ever installed in Ubuntu) but overall xorg is extremely limited to what it can accomplish. It's one thing to hack a system but it's another to actually invest in a company that is supposed to provide basic functionality. It might not be Microsoft but when it comes down to what I'm looking for the Xorg/Xfree86 issue is the only roadblock preventing me from having complete and secure systems. Sooner later I'll probably compile the package which isn't too big of a deal but I had to vent for a second, I apologize if I offended anyone:-\" I could go on describing why each distro sucks but I'll leave that for a later post.

---

