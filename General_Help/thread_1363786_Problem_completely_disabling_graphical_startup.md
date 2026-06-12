---
title: "Problem completely disabling graphical startup"
date: 2009-12-24
forum: General Help
---

### Post by Nazosan on 2009-12-24
I've just set up a system designed to be a server more than anything else.  Most of the time it won't even be hooked up to a screen (most things I'll do via SSH.)  It's almost tempting even to remove X, but for now it's still easier to do some things on rare occasions by hooking it up long enough to do something or other and sometimes a GUI is still the easiest way to do something.  Besides the fact that it's wasting resources to startup with a graphical login, taking longer to start up fully, and so on, I'm running my server on a Compact Flash card via an adapter (in some sizes -- such as this -- it's cheaper than buying a SSD drive.  The cool thing about CF is it is ATA so it needs very little more than a power source and a way to get the connections from point A to point B for IDE interfacing.  It's sad that this standard that truly IS standard is disappearing.)  Given that I'm dealing with solid stat and a relatively cheap implementation with somewhat limited performance (for some reason it won't even let me enable UDMA though the card support 
up to UDMA mode 4) and of course a relatively cheap card can only do so much to begin with, so very rarely I can get some small bottlenecking.  What's more, while the number of total possible cycles is ridiculously high, it still is limited.  I don't really see the need to have things running, reading/writing logs unnecessarily wasting those cycles for absolutely no valid reason.  I can run X any time I want to with startx, so why should it be wasting however small an amount when I can just start it at need?  I actually find it LESS tedious to login via a console and type startx anyway.  (For one, I can do it all via keyboard versus having to use a mouse to select first THEN use the keyboard...)

Anyway, I couldn't remember how I found out once before to disable it.  (I've figured it out once before, but it took googling for hours and a lot of trial and error to do it and this time around google has failed me.)  Of course, I tried the age old method of changing the default runlevel, but I can't even tell how to change that with Xubuntu.  Just in case I tried creating a /etc/inittab with the appropriate line, but no good (I doubt anything even bothers to look at it anymore.)  For whatever reason Xubuntu (and I think all Ubuntu variants really) uses a somewhat unusual method of handling a graphical login.  I tried simply disabling GDM from the startup stuff, but still got the display manager.  (Possibly related to the fact that GDM in the init.d is just a link to the main startup script?)  When that failed, I tried actually completely removing GDM.  Well, this partially works, but, X is still running on startup.  It's not running correctly mind you, but in an even more annoying manner.  First, it's on tty2 for some odd reason.  Second, it's using some video mode my screen can't accept (it's 1440x900 native hooked up to VGA for the server, so should accept anything standard up to 1024x768.)  I can't really see what's going on there even obviously, though I presume it's not actually doing a graphical login so much as trying to.  I must manually kill X if I don't want it running or if I want to do anything with a GUI.  When I run X normally via startx, it still shows up correctly in 1440x900 as it should, so it is configuring correctly (or at least able to under normal conditions.)

Any thoughts on how to get rid of that?

---

### Post by Dark_Stang on 2009-12-24
Step 1. Install BUM (Boot Up Manager)
Step 2. Disable the GUI processes.
Step 3. ????
Step 4. Profit. 

Or...
Step 1. Install server edition.
Step 2. Eat pie.

---

### Post by efflandt on 2009-12-24
Doesn't a (recovery) selection in the grub menu do it for you?  Hint **single** as a kernel boot parameter (and forget "splash").

Also you should be using tmpfs for /tmp, like bootable USB iso does to minimize writing small files that disappear next boot anyway.  /etc/fstab example:

tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by falconindy on 2009-12-24
Append 'text' to the kernel options in Grub.

---

### Post by Nazosan on 2009-12-24
> **Dark_Stang said:**
> Step 1. Install BUM (Boot Up Manager)
Check.

> Step 2. Disable the GUI processes.
Like I said, I've already disabled it.  Is there something else specifically I'm supposed to disable from that list?  Otherwise this looks to be the same thing I've already been doing, just a graphical frontend for the same task.

> Step 1. Install server edition.
Hmm...  I've already gone through some lengths to setup this copy.  Besides perhaps a better default setting in something like this aspect, what benefits are there to the server edition to make it work starting all over?

EDIT:  Lol, fast posters.
> **efflandt said:**
> Doesn't a (recovery) selection in the grub menu do it for you?  Hint **single** as a kernel boot parameter (and forget "splash").
Isn't that "single user mode"?  As in something you'd use only for recovery/etc normally?

> **falconindy said:**
> Append 'text' to the kernel options in Grub.
Ah, I'll give this a shot.  Except I'm using extlinux (the real one, not the damaged modified crap in the repository.)  I'll go check that now.

EDIT2:  That did it.  Thanks.

---

