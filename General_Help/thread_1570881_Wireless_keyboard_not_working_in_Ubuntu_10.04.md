---
title: "Wireless keyboard not working in Ubuntu 10.04"
date: 2010-09-08
forum: General Help
---

### Post by Hot_Sauce on 2010-09-08
ok my wireless mouse is working perfectly fine but they keyboard does not works after typing one or two letters and then it stops working.

How do I fix this :(

---

### Post by Herman on 2010-09-09
:D Hello Hot_Sauce,
I'm afraid I don't know much about wireless keyboards and mice. 
I always  use the wired kind myself. 
I do have one wireless mouse, and sometimes I  have trouble with it, so I don't use it very often.
Apart from the usual 'check the batteries are  charged' and 'follow the instructions in the keyboard owner's manual' I  don't really know what to suggest.  
My wireless mouse is moody and tempramental and it put me off purchasing or using any more wireless products. 

I presume you have determined that the problem is definitely a Ubuntu  problem by trying the same keyboard in the same computer with a  different operating system or in a different computer altogether?
As far as I know, a mouse is just a mouse and a keyboard is just a keyboard as far as Ubuntu is concerned. Maybe I'm wrong, but I imagine it's up to the hardware vendor to make sure the hardware is made to comply with certain agreed protocols, so if your wireless keyboard communicates with an antenna or wireless receiver of some kind that's plugged into a USB port maybe, as far as your computer is concerned it would just look like any other USB keyboard. I imagine that would be the case, but like I said, I could be wrong because I'm just guessing really.

We can install 'drivers' for special hardware in Linux if somebody has  taken the trouble to write a Linux driver for the particular device, but  mostly that's reserved for expensive items like fancy video cards. 
For  most ordinary stuff like keyboards, monitors and mice and ordinary video  cards, the drivers come built in to the Linux kernel. 
My understanding  of the Linux kernel is that it is essentially a big ball of drivers for  all kinds of hardware.
If it was working up until recently and then suddenly it stopped  working, it could be there's a problem of some kind in a new kernel you were given during an update.
Try booting an older kernel  and see if that helps. To do that you just need to stop at your GRUB  Menu when your computer is booting and scroll down to an older kernel  and boot Ubuntu with the older kernel and see if your keyboard keeps  working. If you're lucky it might solve your problem. If so, avoid booting by the present  kernel and some day after another kernel update try that new kernel and  see if it works with that one.

I'm curious about how you get along, so let me know, I hope you can fix it.

Regards, Herman :)

---

### Post by Hot_Sauce on 2010-09-14
I am not sure on how to toggle with the kernel ?!?!? 

Any other recommendation on how to fix this issue ?

---

### Post by Herman on 2010-09-14
[IMG]http://4.bp.blogspot.com/_vgYI1UA9bvw/TDtaSVWJIKI/AAAAAAAAAYc/sr_nVeR4nAo/s1600/sshot169.png[/IMG]
When you see the GRUB Menu, scroll down two lines and boot your second latest kernel.

The first (top) line is your latest kernel.
The second line is your latest kernel, for recovery mode.
The third line is your second latest kernel, try booting that one or even another one further down your menu and see if some other kernel will work better with your wireless keyboard.

---

### Post by Hot_Sauce on 2010-09-14
> **Herman said:**
> [IMG]http://4.bp.blogspot.com/_vgYI1UA9bvw/TDtaSVWJIKI/AAAAAAAAAYc/sr_nVeR4nAo/s1600/sshot169.png[/IMG]
When you see the GRUB Menu, scroll down two lines and boot your second latest kernel.

The first (top) line is your latest kernel.
The second line is your latest kernel, for recovery mode.
The third line is your second latest kernel, try booting that one or even another one further down your menu and see if some other kernel will work better with your wireless keyboard.

Pardon my amateurish questions but how do I enter the grub menu ? I have the ubuntu 10.04 cd ?

---

### Post by Herman on 2010-09-15
Oh I'm sorry, back in May, the last time we typed, you were preparing to install Ubuntu in a USB external hard drive. I presumed you had already done so.
Unfortunately I don't know how to fix your Ubuntu Live CD right now, but I'll keep your problem in mind and if and when some information on that comes to hand I'll return here to pass it on to you. 

Regards, Herman :)

---

### Post by grigglestone on 2011-09-15
does this thread help?

[http://ubuntuforums.org/showthread.php?t=1546149](http://ubuntuforums.org/showthread.php?t=1546149)

---

