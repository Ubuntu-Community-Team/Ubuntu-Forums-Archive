---
title: "Network Problem..."
date: 2009-11-04
forum: General Help
---

### Post by P_0017 on 2009-11-04
[TOTAL LINUX N00B HERE]

I just installed Ubuntu using wubi on my PC. My PC doesnt have a built in wireless card, so I got a belkin N+ (image below). here's where the problems start...Ubuntu wont register that there is a wireless adapter plugged in, and thus, doesnt scan for networks. The adapter doesnt turn on(the little blue wifi light isnt on(second light down in the picture), but when I switch back to Windows 7, its fine!

Are there any drivers for the belkin N+ that work for ubuntu


PICTURE:










[IMG]http://www.blogcdn.com/www.engadget.com/media/2008/07/7-10-08belkinstick.jpg[/img]

---

### Post by ndefontenay on 2009-11-04
That is one big *** picture!

Anyway. The problem is that this device is not supported by ubuntu.

You can try to see if linux can see it at all for starters by typing the command: lsusb in the terminal (applications>Accessories>terminal)

Here some bad news and some potential solutions (I used ndiswrapper before it worked fine):

[http://www.lockergnome.com/linux/2007/09/13/belkin-wireless-n1-on-ubuntu/](http://www.lockergnome.com/linux/2007/09/13/belkin-wireless-n1-on-ubuntu/)

Nico

---

### Post by x C0MMAND0 x on 2009-11-04
Try going to System > Administration > Hardware Drivers and seeing if there is anything listed in there?

---

### Post by soapBAR2 on 2009-11-04
There's a strong possibility that there aren't drivers for it. Although it's becoming less and less of a necessity, if you're using linux, you should google or visit [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) to see the state of drivers before buying hardware, as not all vendors are as linux-friendly as we'd like them to be. Some companies are commonly known to be particularly bad or particularly good - for example, Intel generally has a pretty good reputation, whereas Atheros generally has a pretty bad reputation.

---

### Post by P_0017 on 2009-11-04
D: I highly doubt that there are drivers aswell......what other USB wireless adapters do you recommend?

---

