---
title: "Emacs highlighting issue after upgrade to 9.10"
date: 2010-01-30
forum: General Help
---

### Post by mafauq on 2010-01-30
Hi all, 

I recently upgraded from 9.04 to 9.10 and since the upgrade, emacs has been 
behaving differently.  Specifically, when I left-click on the scroll scrollbar, if this 
causes the cursor to move, then the region betw where the cursor was and where it 
is becomes highlighted.  This also happens if I left-click and drag along the scrollbar.

It didn't behave like this before and I find it very annoying!  
I've tried turning transient-mark mode on/off but that doesn't make a difference.

This is the version of emacs that I am using:
  
  GNU Emacs 23.1.50.1 (i486-pc-linux-gnu, GTK+ Version 2.18.0)
  of 2009-09-27 on palmer, modified by Debian

I've tried removing and re-installing emacs and I've deleted my .emacs file and .emacs.d directory, 
just to make sure there was nothing there causing this.

Oh also, when I start emacs I get the following message in the terminal 
  
  (emacs:3741): GLib-WARNING **: g_set_prgname() called multiple times

I don't know if that is related, but it's also new since the upgrade to 9.10

Any help would be greatly appreciated!

---

### Post by jpkotta on 2010-02-08
The thing you're describing is the region, highlighting is something different in Emacs.  

It sounds like the region is active before you start scrolling.  Since scrolling will move the point (text cursor), it will change the region (one end of the region is always the point).

You might want to try starting Emacs with the -Q or -q option.  -q starts it without any of your config files (e.g. ~/.emacs).  -Q starts it with only base config files -- it skips any packages you've installed with apt, e.g. AUCTeX.  

To get a workaround, you could try advising the command that gets run when you click/drag the scroll bar so that it deactivates the region.

I noticed the GTK errors on my 9.10 install too, it's probably not a big deal.

---

