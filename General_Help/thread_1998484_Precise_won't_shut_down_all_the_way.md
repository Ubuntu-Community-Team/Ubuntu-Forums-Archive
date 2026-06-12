---
title: "Precise won't shut down all the way"
date: 2012-06-06
forum: General Help
---

### Post by radiors on 2012-06-06
I have searched the forum, but have not found this exact problem.  I have a fresh install of 12.04 64.  Computer has an AMD FX 4100 chip on a Gigabyte 78LMT-S2P motherboard.  4 gigs of memory.

Ubuntu was installed after Windows 7 so I have a dual-boot.

All is working very, very well with Precise.  No problems, except for one, which arose several days after my initial install.  I did not have this problem until a few days ago.

When I shut down, the computer hangs at the final Ubuntu splash screen with white dots.  I used _shutdown now_ from terminal and this is the error I got.

modem-manager [2915]  Could not get the system bus.  Make sure bus daemon is running.  Message:  Failed to connect to socket /var/run/dbus/system_socket_bus.  No such file or directory.

This is a very annoying problem on a system that otherwise is running flawlessly.

Any ideas are greatly appreciated?

Thanks

---

### Post by VMC on 2012-06-06
Couple of links related to your problem

1) [http://askubuntu.com/questions/87576/slow-shutdown-due-to-modemmanager-and-nm-dispatcher-action](http://askubuntu.com/questions/87576/slow-shutdown-due-to-modemmanager-and-nm-dispatcher-action)

2) [http://ubuntuforums.org/showthread.php?t=1355981](http://ubuntuforums.org/showthread.php?t=1355981)

I saw reference to this during the precise cycle.

---

### Post by radiors on 2012-06-07
I wish I could say that any of these things worked for me.  I tried all the options in the threads and I'm still having the same problem.

In a fit of sillyness (stupidity) I even removed Network Manager.  That didn't do anything either, except give me a few hours of joy figuring out how to re-install it without having a network connection anymore.  

Also, hate to admit it, but Windows boot and shutdown is working fine.

Any other ideas?

Thanks.

---

