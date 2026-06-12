---
title: "Opera ~ error while reading system fonts"
date: 2012-06-22
forum: General Help
---

### Post by neu5eeCh on 2012-06-22
Opera no longer works after latest update.

Is anyone else getting the "system fonts" error?

/usr/lib/opera/opera got signal SIGSEGV at address 08BE6B09

---

### Post by vasa1 on 2012-06-22
> **VTPoet said:**
> Opera no longer works after latest update.

Is anyone else getting the "system fonts" error?

/usr/lib/opera/opera got signal SIGSEGV at address 08BE6B09

It's working for me. What do you have to do to see the error?

---

### Post by neu5eeCh on 2012-06-22
> **vasa1 said:**
> It's working for me. What do you have to do to see the error?

Any attempt to actually *use* Opera causes the error. ;-) I only see the error message when starting it in terminal, if that's what you're asking? Otherwise, if one tries to start it from the menu, one doesn't see anything at all, and that includes Opera.

---

### Post by d2btoo on 2012-06-22
Are you using KDE by any chance.... Opera 12 has some problems in KDE (may or may not be related to your problem, though)

*source Opera forum.
Opera 12.01 fixed them afaik.
[quote=VTPoet]
I only see the error message when starting it in terminal, if that's what you're asking? Otherwise, if one tries to start it from the menu, one doesn't see anything at all, and that includes Opera.[/quote]

wouldn't **.xsession-errors**, will show them!

---

### Post by neu5eeCh on 2012-06-22
> **d2btoo said:**
> Are you using KDE by any chance.... Opera 12 has some problems in KDE (may or may not be related to your problem, though)

*source Opera forum.
Opera 12.01 fixed them afaik.


wouldn't **.xsession-errors**, will show them!

I'm using Xubuntu. I noticed that thread about a hidden .kde directory with permissions incorrectly set to root, but I don't have a .kde directory. I also googled "error while reading system fonts", and only found one lead written in Polish (I'm guessing).

---

### Post by vasa1 on 2012-06-22
> **VTPoet said:**
> Any attempt to actually *use* Opera causes the error. ;-) I only see the error message when starting it in terminal, if that's what you're asking? Otherwise, if one tries to start it from the menu, one doesn't see anything at all, and that includes Opera.
Right. Opera, as I said, works for me so I don't have to troubleshoot via the terminal. If it's of any significance, I'm not on Xubuntu but in an Xfce 4.10 session (on Ubuntu 12.04).

IIRC, you had some problems with another browser recently. No connection?

---

### Post by d2btoo on 2012-06-22
@VTPoet: I would post on opera forum..... now there was a switch particularly for troubleshoot font problems.... can't remember it atm :sad:

---

### Post by neu5eeCh on 2012-06-22
> **vasa1 said:**
> Right. Opera, as I said, works for me so I don't have to troubleshoot via the terminal. If it's of any significance, I'm not on Xubuntu but in an Xfce 4.10 session (on Ubuntu 12.04).

IIRC, you had some problems with another browser recently. No connection?

No connection, I don't think. A while back I noticed that my laptop's memory (3 Gigs) was being eaten alive. The monster, whatever it was, moved onto half my swap drive until it took me 2 minutes to shut down Xubuntu. Turns out, both Chrome **and** Firefox slowly bloat and bloat and bloat. I don't restart my system, only suspend, so FF & Chrome can, in effect, be up and running for a week at a time. Every time I use Flash or HTLM5, both browsers grab a little more memory and don't let go. They're like *memory-quicksand*. If I don't restart FF or Chrome (which I now regularly do) FF will slowly consume half a gig to a gig's worth of memory. It's weird. Just recently, FF was hoarding half a gig's worth of memory. I restarted it (re-opening the same web pages) and it returned to about 175 MIB. It's now slowly creeping back up. It's at 228 MiB right now.

Incidentally, Conky does the same thing. At the moment, Conky is hoarding 246 MiB. 

And...

There...

 Just restarted Conky. It's now at 1.6 MiB!!!

**Edit:** Just noticed there is a bug associated with this Conky memory leak:

[https://bugs.launchpad.net/ubuntu/+source/conky/+bug/952637?comments=all](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/952637?comments=all)

---

### Post by neu5eeCh on 2012-06-22
Every time I p-ss around with this browser, it stops working, I can't use it with WordPress, can't use it with Java, can't use it with Fonts, can't... yadda, yadda. Piece of junk.  Removed Opera.

Solved. O:)

---

