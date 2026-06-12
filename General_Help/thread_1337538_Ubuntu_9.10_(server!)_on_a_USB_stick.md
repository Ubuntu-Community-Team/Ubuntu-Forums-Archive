---
title: "Ubuntu 9.10 (server?!) on a USB stick"
date: 2009-11-25
forum: General Help
---

### Post by slasc on 2009-11-25
Recently, we had a machine at our office in which the hard drive died.  Rather than replace the drive, they replaced the whole machine.  Now, as a result, we have a ~2ghz. Athlon with about a gig (or just under) in Ram....and no hard drive.

So, being the adventuress sort, I decided I wanted to purchase (for about $15) a usb (flash) thumb drive and put Ubuntu server on there.  At the time when I started this, I was going to set up a VPN server on said machine, but I have since found an easier solution with a different machine.  Even so, having already determined to try this, I went and installed 9.10 server onto the thumbdrive with NO SWAP DRIVE.  It has gone remarkably smooth.  However, I am wary (and curious) as to the frequency of read/write operations conducted by the OS, and I am wondering if there are some tweaks I can do to minimize the potential number of write operations before they damage the thumb drive.  (if the drive dies, so be it, but I would rather it not)  I understand I could have just used the USB live disk creator utility, but I wanted the server kernel.  As I said above, I am the adventuress sort.  This is an experiment for me.

So, does anyone know how to determine the frequency of the read write operations and how I can measure that to get an idea on the current setup's lifespan?  I would also be curious as to ways I can cut down on those write operations which USB thumb drives tend to die early deaths from.  Any advice?

Kelly

p.s. - I did also install a GUI.  I know, who installs a GUI on a server OS?  Cut me some slack here!  This is an experiment!  :)

---

### Post by egalvan on 2009-11-25
I've seen tutorials on how to minimize writes to solid state hard drives.


here is one...

[http://robert.penz.name/137/no-swap-partition-journaling-filesystem-on-a-ssd/](http://robert.penz.name/137/no-swap-partition-journaling-filesystem-on-a-ssd/)

---

### Post by slasc on 2009-12-01
Thanks!  That looks like exactly what I was looking for!!!  :)

---

