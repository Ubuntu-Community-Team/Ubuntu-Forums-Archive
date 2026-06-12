---
title: "xterm not refreshing"
date: 2011-05-17
forum: General Help
---

### Post by kresnik7 on 2011-05-17
I recently upgraded from xubuntu 9.04 to 11.04, and it seems xterm is either incorrectly configured for the new desktop or not working right.  After a bit of typing, xterm stops refreshing, and only the first few chars or words are shown until I manually refresh xterm (then, whatever I'd written shows up correctly).

Steps to reproduce
1. Open xterm, basic command prompt shows up
2. Type "hello, this is a test", xterm only shows "hello, th"
3. Press 'ctrl-l' or click outside the xterm window, xterm updates with full "hello, this is a test"

Already tried dpkg-reconfigure with no success.

Attached is the output from "appres XTerm" and "infocmp"

---

### Post by itcotbtoemik on 2011-05-18
The most likely problem is that you upgraded and got the
"new" desktop, which is based on compiz.  There are apparently
a lot of problems with it interacting with X applications
(more than xterm, though xterm is the most often reported
due to widespread use).

---

### Post by kresnik7 on 2011-05-18
Under XFCE lancher->Settings Manager->Window Manager Tweaks->Compositor, "Enable display compositing" is disabled, as is everything else on this page.

---

### Post by Jose Catre-Vandis on 2011-05-18
Do you mean xterm or xfce4-terminal?

xfce4-terminal should be installed by default. Does it have the same problem?

---

### Post by kresnik7 on 2011-05-18
The issue was with xterm.  xfce4-terminal was not installed, but I've installed it now and it does not appear to have this same problem.

Thanks Jose!

---

### Post by DGPickett on 2011-12-16
I have this too, worse, with fragments of scrolled data and failure to scroll to the bottom.  I have to scroll around to make it refresh, or the like.

I have all the latest software and Ubuntu updates, latest Ubuntu O/S, normal distribution, not pre-release.

I looked on the software installer for this tool, and did not find it.  Will someone fix the xterm.  It seems sad to mark this solved when it is acknowledged as still broken (for the xterm, a rather traditional thing to support on any new X server).  Can I pick another X Server that can handle xterm robustly?

---

