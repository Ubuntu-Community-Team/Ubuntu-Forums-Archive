---
title: "Intel video card"
date: 2012-03-22
forum: General Help
---

### Post by Rainersxd on 2012-03-22
Hellow agen !
 I have problem with my video card drivers for linux.
 I have video card: Intel HD graphic. And I don't anderstand why my minecraft graphics are so lined ( I mean: there are many lines over my game, and image are "jumpig" sory I don't now how it is writing write).
 Some gases what is wrong ?  
P.S. My computer telling my that the video card is called: sandy bridge !

---

### Post by UltimateCat on 2012-03-22
Open a terminal and put in the command:
```
lspci

```

This is a command for displaying info. about all PCI buses in the system and all devices connected to them.  It's useful when you want to diagnose problems or when you want to report bugs related to PCI devices.

When I found out what card I had I was able to search for the right ATI/AMD driver.

[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

---

### Post by Rainersxd on 2012-03-22
Well, my computer saying that all is ok... maybe the minecraft aren't scripted correctly for Linux ?
Or on what I'm sopost   to watch in Terminal ?

---

### Post by grahammechanical on 2012-03-22
See, this article written about 3 months ago.

[http://www.phoronix.com/scan.php?page=article&item=intel_sandy_2011&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_sandy_2011&num=1")

And this link

[https://wiki.ubuntu.com/Kernel/PowerManagementRC6]("https://wiki.ubuntu.com/Kernel/PowerManagementRC6")

It is my guess that your video card is in advance of the Linux support for your video card. These things take time even with Intel developing open source drivers.

Regards.

---

### Post by Rainersxd on 2012-03-22
I'm sory, but I still don't understand what I'm sopost to do.
Is there something smaller and faster to do ?

---

### Post by Mark Phelps on 2012-03-24
What you are "supposed to do" -- is open a terminal, enter "lspci" (without the quotes) -- and look for the output line containing "VGA".  That will show the make and model video chip you're using.

Post that result back here.

Without knowing that, we can only guess.

---

