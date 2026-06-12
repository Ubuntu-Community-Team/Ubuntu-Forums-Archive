---
title: "Brother HL2170W networked printer stopped working"
date: 2012-06-25
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-06-25
Hi All,

I installed my Brother HL-2170W printer via our wireless router, and it worked fine till very recently.

Now, it just sits there with print jobs remaining in the queue and does nothing.

On my wife's windows work laptop, it prints just fine (32 bit dell laptop). 

It continues to run fine for my daughter's 64 bit Dell laptop.

But, for my old 32 bit P4 processor desktop, there is no printing, no errors, just sits there forever.

I've done some troubleshooting and think I might have found the problem, but am not sure how to go about fixing it.

Using my system, I can connect to the printer through the browser, after typing in the printers IP address (192.168.1.1). 

When I go to system>printing, I can see the printers icon, with a large green check mark, so the printer driver is there.

From system>printing>properties, I see that it looks like it's connected to the parallel port, not the wireless. In other words, the 'Device URI' says 'parallel:/dev/lp0'. I'm fairly certain this means the computer thinks it's connected to the parallel port.

When I try to change the  'Device URI' to http:/192.168.1.39, I get an error.

I think I can delete the existing driver and then reinstall it, but don't know if that's the best thing to do.

Would appreciate any suggestions.

Art

---

### Post by goodbye-windows(tm) on 2012-07-01
I deleted the printer driver that was corrupted somehow, and reinstalled. Took me all of 60 seconds, or less.......including the download time for the driver!!! 

Happy forumizing (is that a word??)

Art

---

