---
title: "Can I un-fix Grub?"
date: 2011-08-30
forum: General Help
---

### Post by BuddyThirteen on 2011-08-30
I ran the script to fix the Grub on both of my computers. On one of them, it's working flawlessly. But on the other, it has introduced a random-logout bug.

Or at least, this is what I've inferred from what I've found about the logout bug. Seems it starts when people "fix" Grub, and goes away if they un-fix it. But I don't know how to un-fix it. I'd be fine with an ugly bootup if it means I don't get randomly logged out. It wouldn't be such a big deal if it didn't also change the resolution when it logged out, so I can't just log back in, I have to reboot.

Any ideas?

---

### Post by dino99 on 2011-08-30
open synaptic to remove/purge ALL the related installed grub packages, then reinstall grub-pc and set it on MBR (/etc/sdx, not /etc/sdxx; where is x is the booting partition)

---

### Post by coffeecat on 2011-08-30
A random logout-bug associated with grub? :-k

I don't see how that could be. Grub is a bootloader and has stopped doing its thing long before you even get to the login screen, let alone while you are logged in. Can you post some links to descriptions of this alleged bug that appears when you "fix" grub and disappears when you unfix it? And what was the script that apparently fixed grub? Can you post a link or description? What was wrong with grub before you fixed it?

By random logout-bug, I guess you mean that you are working in the GUI and you are suddenly taken to the log in screen. Can you give us some more details?

---

### Post by BuddyThirteen on 2011-08-30
Oh dip, I confused Grub with Plymouth. That's the thing that got fixed. Y'know, so it's not ugly after installing proprietary drivers. That's the thing that some people were blaming.

While googling to find the reports where people said it was the Plymouth fix, I found this:

[http://www.mjfox.ch/wordpress/ubuntu-11-04-and-that-random-logout-problem/](http://www.mjfox.ch/wordpress/ubuntu-11-04-and-that-random-logout-problem/)

So the Plymouth fix may be just correlation without causation. But people seemed to think that doing this - [link]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/") - was related somehow.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/760695](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/760695)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490)

Seems most people are having the problem with their laptops, though my laptop is the one that's operating perfectly, and the desktop is the one being buggy.

The solution above seems to be more of a workaround than an actual fix, but I'll give that a try unless anyone can offer anything else. Or possibly tell me that option b and c are a bad idea.

For me, it seems to only happen when the computer is idle (i.e., not browsing the internet, like most people report), so it may indeed be something about power saving being broken or some such.

---

### Post by coffeecat on 2011-08-30
Those are interesting links - thanks.

I'm really glad it wasn't grub causing random logouts! That would have made me rethink the whole of my Linux experience. :)

And I don't think it's related to Plymouth either. The ugly Plymouth with proprietary video drivers has been going on since Lucid. The random logouts seem to be new with Natty and related to the xserver synaptics package.

I see that some people are still getting the ugly Plymouth with Natty. Using a Geforce 8400GS card, I was pleased to see that my Natty Plymouth was OK with the proprietary nvidia driver and I assumed the issue had been fixed. Clearly not, and it must depend on your graphics chipset.

---

### Post by BuddyThirteen on 2011-08-30
Yeah, even with proprietary drivers, my laptop works flawlessly. Nice-looking Plymouth, and no random logouts. The older desktop is where the problems were.

So I fixed Plymouth, and then random logouts started. So you can see why I thought there might be some credibility to those claims that they were related. 

Unlike everyone else, though, mine seems to only happen when the computer's idle. For example, I can watch shows on that thing all day long (which is really all it's for, anyway) and nothing happens. But if the show ends, it goes to screensaver, and within ten minutes or so, logout occurs. And stupid changing on resolution, whatever that's about.

---

