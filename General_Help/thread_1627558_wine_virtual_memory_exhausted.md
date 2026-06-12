---
title: "wine: virtual memory exhausted"
date: 2010-11-21
forum: General Help
---

### Post by mathiaho on 2010-11-21
Hi

Wine is useless on one of my computers running lucid 32bits.
If i try to run a program through wine or even winecfg I get the error:
wine: virtual memory exhausted

Any Ideas

I have tried shredding all the files in the .wine directory, removing every package that have anything with wine in their name in synaptic, and sudo aptitude purge wine.

problem persists:confused:

Please help!

---

### Post by hakermania on 2010-11-21
Give RAM info

---

### Post by mathiaho on 2010-11-21
Thanks for the fast answer!

two ddr2 1gig sticks from geil... Any specific info you want (and commands to find that info)?

btw Wine has worked perfectly before

---

### Post by hakermania on 2010-11-21
try removing the .wine directory in your home folder. If this does not work then these are some useful links:
[http://opendmi.units.it/open/?q=aggregator/sources/34](http://opendmi.units.it/open/?q=aggregator/sources/34)
[http://archives.free.net.ph/message/20081122.172720.87b4190d.el.html](http://archives.free.net.ph/message/20081122.172720.87b4190d.el.html)

---

### Post by mathiaho on 2010-11-21
I've already tried removing my .wine folder, and I have reinstalled wine multiple times. I've searched as thoroughly as I can after the error "wine: virtual memory exhausted", but have been unable to find any info.

Can't find any useful info in your links.

Thanks though

---

### Post by mathiaho on 2010-11-24
*bump*

Anyone know any solution?
I would really like not having to reinstall ubuntu

Thanks

---

### Post by JackSchnippes on 2010-11-28
[I had the same error]("http://ubuntuforums.org/showthread.php?p=10172722#post10172722")! But don't know if you use the same wine version as me. I use wine with a realtime patch from falktx's PPA. Turns out my user wasn't added to the audio group and hence did not have realtime priorities. After making my user a member of the audio group (System -> Administration -> Users and Groups) and logging out and in again (and of course using a realtime kernel) the issue was resolved... So for others to help you, you might want topost your wine version!

---

### Post by mathiaho on 2010-11-28
> **JackSchnippes said:**
> [I had the same error]("http://ubuntuforums.org/showthread.php?p=10172722#post10172722")! But don't know if you use the same wine version as me. I use wine with a realtime patch from falktx's PPA. Turns out my user wasn't added to the audio group and hence did not have realtime priorities. After making my user a member of the audio group (System -> Administration -> Users and Groups) and logging out and in again (and of course using a realtime kernel) the issue was resolved... So for others to help you, you might want topost your wine version!

It worked! Thank you so much!

Seriously, you have saved me from a lot of pain and suffering :P

 I'm running wine and wine-dev 1.2, and I have the generic kernel. I have given the audio group realtime priorities, though, so I guess that's the problem.

Again: Thanks!

---

### Post by gja on 2011-01-23
Worked for me too.

Dell D600 (512MB RAM)
Ubuntu 10.04 with Wine 1.3.8 is now working.

---

### Post by bikodog on 2011-08-20
Worked for me. This problem has followed me on two installs of kxstudio Lucid Lynx 10.04 on two machines. Simple solution!

---

### Post by jaccarmac on 2012-02-10
In updating 11.10, wine got broken. Setting myself up in the audio group has not fixed the problem.

---

### Post by OutThisLife on 2012-06-23
> **jaccarmac said:**
> In updating 11.10, wine got broken. Setting myself up in the audio group has not fixed the problem.

Ever find a solution?

---

