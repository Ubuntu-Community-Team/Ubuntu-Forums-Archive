---
title: "Strange GUI behavior in Code::Blocks after 11.10 upgrade"
date: 2012-01-18
forum: General Help
---

### Post by hailtothethief on 2012-01-18
Hey guys.

I've been using Code::Blocks for about a year and a half now for all of my C/C++ development. It's awesome, I can't say enough about it. But since upgrading to 11.10 I've run into a problem.

My GUI renders as in the screenshot. It works 95% correctly, all menus behave properly, I can edit files as normal, but the GUI only renders on a small portion of the screen (an 800x600 area I believe). I've tried resizing and maximizing the window, to no avail. I can't get it to draw any more than what you see in the screenshot. The interface is also very choppy and slow to respond, whereas on 11.04 C::B was always very responsive for me.

At first I thought it was due to some bug in SVN (I've been using fresh SVN builds for quite some time) so I uninstalled the SVN version and installed from the repo. I got the same exact problem, so then I tried building from the repo's source package, still no luck.

I really want to keep using C::B. Does anyone have any clue how I might fix this, or even what might be causing the problem? I'm pretty good at solving issues like this once I know where to start, but I'm just totally clueless in this case.

The console output contains nothing but the standard log messages about loading plugins etc. I've also already tried rm'ing my config directory.

For now I'm falling back to gvim and Makefiles (as you can see in the screenshot), so please help if you can.

Thanks.

---

