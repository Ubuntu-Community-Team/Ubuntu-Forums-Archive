---
title: "Help with IR Remote Control!! Completely stumped!!"
date: 2012-04-19
forum: General Help
---

### Post by hector1229 on 2012-04-19
So I just purchased a new IR Remote control to use with my HTPC recently and im having a really weird problem. I received my remote and proceeded to connect the usb IR Receiver to my HTPC, put batteries in the remote and pressed the power button to see if the remote worked out-of-box with my HTPC but somehow the remote is controlling my laptop?? So my laptop has a built-in IR receiver (I've now assumed as much) but i have no idea how to disable it or the remote. I do not have LIRC installed and have not been able to find how Ubuntu 11.10 handles IR Devices. Any help or points in the right direction would be greatly appreciated.

---

### Post by Shplad on 2012-05-19
I'm just learning about IR (infrared, as in remotes) in Linux myself, and it can be very confusing. 

In your situation, what OS is your laptop running? Windows? Linux?

If you want the remote to control your laptop AS WELL AS your other computer, it could get a little more complicated. If not, why not just go into the laptop's OS configuration and disable the laptop's infrared receiver. If it's running Windows, you can disable devices like that in Device Manager. If in Linux, it would probably be easiest for a newbie to disable the hardware in the laptop's hardware setup utility. It can be disabled in Linux, but I don't know how. Can someone else give more info. on doing this?

I found this article helpful.:
**HOW TO GET A SEAMLESS REMOTE EXPERIENCE**
[http://forum.xbmc.org/showthread.php?tid=104541](http://forum.xbmc.org/showthread.php?tid=104541)
It explains that most HOWTOs, walk-throughs and tutorials for configuring LIRC assume older versions of Linux or the Linux kernel. 

But with newer versions of the Linux kernel, (such as that included in Ubuntu 11.1), things changed. There is now a separate driver for IR built into the kernel.  That means that many of the tutorials can make things confused or messed up.

lirc "proper" and the driver for IR built into the kernel can conflict with each other. Sometimes, you're okay, but other times, the results can be unpredictable or confusing.


Shplad





> **hector1229 said:**
> So I just purchased a new IR Remote control to use with my HTPC recently and im having a really weird problem. I received my remote and proceeded to connect the usb IR Receiver to my HTPC, put batteries in the remote and pressed the power button to see if the remote worked out-of-box with my HTPC but somehow the remote is controlling my laptop?? So my laptop has a built-in IR receiver (I've now assumed as much) but i have no idea how to disable it or the remote. I do not have LIRC installed and have not been able to find how Ubuntu 11.10 handles IR Devices. Any help or points in the right direction would be greatly appreciated.

---

