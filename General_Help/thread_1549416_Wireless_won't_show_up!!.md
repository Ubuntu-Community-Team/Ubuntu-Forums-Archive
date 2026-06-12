---
title: "Wireless won't show up!!"
date: 2010-08-09
forum: General Help
---

### Post by blindmelon1091 on 2010-08-09
Hey all.

I recently got a new Prostar laptop and have installed Ubuntu on it as the os. No wireless network is available. I tried to enable the wireless and then install the proprietary driver but when I opened Hardware Drivers it said "Downloading  package indexes failed, please check your network status. Most drivers  will not be available."

Can anyone more knowledgeable than myself please tell me why this is happening? What can I do to make my wireless work? By the way, my wireless is an   				Intel Ultimate-N 6300 Wi-Fi.

Thanks in advance guys.

---

### Post by earthpigg on 2010-08-09
hi,

google search for "Intel Ultimate-N 6300 ubuntu" returned [this]("http://ubuntuforums.org/showthread.php?t=1420901") thread as the first result.

have you tried that?

have you tried anything else?

---

### Post by blindmelon1091 on 2010-08-09
Thanks for the response, but unfortunately I already read that forum post. I downloaded Karmic (at least I think that's what it was, the site was confusing) I got it from herehttp://packages.ubuntu.com/karmic/linux-backports-modules-karmic-generic-pae  and now I have no idea how to install it on my laptop. Can you please tell me in layman, step by step terms what to do now? Honestly, I'm not very up on computer/tech jargon. Thanks for the patience to whoever can do this.

---

### Post by TBABill on 2010-08-09
Have you tried plugging into your router directly via ethernet cord, then trying to install the driver? You can't download it without a connection of some sort in place.

---

### Post by blindmelon1091 on 2010-08-09
I burned the file on a cd and then pulled it up, should that work? If so how do I install it from there. I'll go the ethernet route if I have to, but I've already burned the cd so I like to try that first.

---

### Post by TBABill on 2010-08-09
The CD is to install Ubuntu. In order to get some wireless drivers you need to connect via ethernet and let the system update and download available drivers.

If you're trying to update via a single file from CD, hopefully someone else can offer advice.

---

### Post by oleink on 2010-08-09
> **TBABill said:**
> The CD is to install Ubuntu. In order to get some wireless drivers you need to connect via ethernet and let the system update and download available drivers.

If you're trying to update via a single file from CD, hopefully someone else can offer advice.

Yeah.  The broadcom bcm43xx for example was included in 9.04 and maybe 9.10?  But now it is not on the cd so like he said be sure to try plugging into a router and downloading that way because I was confused when I did a fresh install on the arrival of 10.04 (ps the bcm43xx is just an example because that was my driver.)

---

