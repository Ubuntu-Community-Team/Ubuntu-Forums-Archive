---
title: "acpi causes graphics to slow down"
date: 2010-01-02
forum: General Help
---

### Post by lipos on 2010-01-02
I have to use acpi=off because my PC is crushing/freezing during installation and 2 mins after boot up.
Currently I'm using acpi=ht to enable second CPU.

The problem is that my Intel graphic card is slow and Xorg is taking a lot of CPU.
I'm also not able to enable compiz when disabling acpi.
The biggest problem is the MythTV that is so slow in the menu area alone that I'm not watching any TV in it lately.

When I'm not, it's crushing, no CPU spikes, no strange behavior just crushing without any logs.

Any idea how I can troubleshoot it?
Ubuntu 8.10 was running well on the box.

---

### Post by lipos on 2010-01-03
Here's my fix:

I left acpi=ht in grub (two CPUs are used) and reverted to 8.10 intel drivers using:

[http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html]("http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html")

I see two CPUs, and graphics runs well.

Hope this will help someone since I lost a lot of time on it :)

---

