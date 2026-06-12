---
title: "Growing tired of  Linux/Ubuntu's lack of hardware support"
date: 2009-12-16
forum: General Help
---

### Post by Nonsense on 2009-12-16
I know that the poor hardware support many linux users are experiencing are due to the fact that most hardware vendors doesn't give a hoot about linux and therefore does not supply any drivers.
I, for one, am growing increasingly tired of this.
I have spent a large amount of time and money investing in the "proper" hardware, just to find out that the next kernel update removed support for that device or that the list of supported hardware was flawed.
I have tried again and again to make hardware vendors aware of the problem, but I have recieved little or no feedback.
This needs to be addressed. Unless the Linux community can make their voice heard in the hardware industry, LINUX HAS NO FUTURE. If something just doesn't work "out-of-the-box" (more or less) the system is doomed.

For the moment this is the hardware I can't get to work:

    * A Canon scanner, modell 4200f (I know Canon has a history of bad support, but I can't be the only one that doesn't wan't to buy a new scanner just because a proper driver is missing)
    * MOTU Traveler soundcard (MOTU to seems to have a history of bad hardware support and have replied "no" to each enquiry on the subject of linux drivers)
    * Nikon F60 camera (no support for reading the memory card in the camera, have to remove it each time)
    * Microsoft LifeCam VX-1000 (supposed to work, but after a kernel update it doesn't)


LINUX NEEDS TO SUPPORT MORE HARDWARE!
This needs to be top priority

---

### Post by philinux on 2009-12-16
As for the camera. Have you tried gthumb, it's in the repos.

I had this exact problem in Intrepid but jaunty and karmic have been great with my canon g5 camera. I had to but a cheap card reader while running Intrepid.

In fact installing Karmic might get you better support or try the livecd first to be sure.

---

### Post by endeavormac on 2009-12-16
I understand your frustration, but this is really not the appropriate place to address this issue.

When support for hardware is placed in the linux kernel, it is done by either A) The hardware manufacturers, or B) individuals with the know-how and desire to make that piece of hardware compatible with their system.

You should email the hardware manufacturer letting them know you want support for their products in linux, and, if you find someone who is working on a driver independently, send them an email letting them know their work is appreciated and you anxiously await an update.

---

### Post by doas777 on 2009-12-16
> **Nonsense said:**
> I know that the poor hardware support many linux users are experiencing are due to the fact that most hardware vendors doesn't give a hoot about linux and therefore does not supply any drivers.
I, for one, am growing increasingly tired of this.
I have spent a large amount of time and money investing in the "proper" hardware, just to find out that the next kernel update removed support for that device or that the list of supported hardware was flawed.
I have tried again and again to make hardware vendors aware of the problem, but I have recieved little or no feedback.
This needs to be addressed. Unless the Linux community can make their voice heard in the hardware industry, LINUX HAS NO FUTURE. If something just doesn't work "out-of-the-box" (more or less) the system is doomed.

For the moment this is the hardware I can't get to work:

    * A Canon scanner, modell 4200f (I know Canon has a history of bad support, but I can't be the only one that doesn't wan't to buy a new scanner just because a proper driver is missing)
    * MOTU Traveler soundcard (MOTU to seems to have a history of bad hardware support and have replied "no" to each enquiry on the subject of linux drivers)
    * Nikon F60 camera (no support for reading the memory card in the camera, have to remove it each time)
    * Microsoft LifeCam VX-1000 (supposed to work, but after a kernel update it doesn't)


LINUX NEEDS TO SUPPORT MORE HARDWARE!
This needs to be top priority
ok, so the manufacture won't support it. I guess that leaves it to you to write the drivers. after all, that is what you are demanding we do. and no, linux is not doomed.

---

### Post by Nonsense on 2009-12-16
> **philinux said:**
> As for the camera. Have you tried gthumb, it's in the repos.

I had this exact problem in Intrepid but jaunty and karmic have been great with my canon g5 camera. I had to but a cheap card reader while running Intrepid.

In fact installing Karmic might get you better support or try the livecd first to be sure.

Thank you I will try that.
Unfortunatley I like Picasa better :(

---

### Post by Nonsense on 2009-12-16
> **endeavormac said:**
> I understand your frustration, but this is really not the appropriate place to address this issue.

When support for hardware is placed in the linux kernel, it is done by either A) The hardware manufacturers, or B) individuals with the know-how and desire to make that piece of hardware compatible with their system.

You should email the hardware manufacturer letting them know you want support for their products in linux, and, if you find someone who is working on a driver independently, send them an email letting them know their work is appreciated and you anxiously await an update.

I have emailed various hardware manufaturers several times, but the reply is always the same: "no plans for linux drivers". I can't see any change unless we all come together on this. And I think it is not just up the the user community, but also the various foundations and companies that make up the linux milieu.

---

### Post by Nonsense on 2009-12-16
> **doas777 said:**
> ok, so the manufacture won't support it. I guess that leaves it to you to write the drivers. after all, that is what you are demanding we do. and no, linux is not doomed.

I am not demanding any single user to do anything. I am simply saying that if a OS has bad support for hardware it has a very slim chance of survival outside the "hardcore" community. Don't get me wrong, I really like Ubuntu and Linux in general (so much that I all the computers in my home with Ubuntu installed), most of the software is great, but the support for hardware really needs to get better.
I do understand that this is partly up to the hardware industry, but I think the Linux community needs to make extended hardware support their top agenda.

---

### Post by DaVince21 on 2009-12-16
While you might have been growing tired of this, hardware support in Linux is only ever increasing, and actually supports a lot more hardware than, say, Windows Vista simply because drivers only have to be written once (properly) to work forever.

The problem is where either one of the following types of hardware isn't much supported:
- Very new hardware (it's preferably up to the manufacturers, or else open-source developers, to make drivers);
- Legacy hardware that might not have been used too much in the past (fat chance on still getting drivers for that, though if the model is generic enough it might automatically gain support at some point).

Thing is, most companies don't actually focus on Linux drivers because of its tiny market share. This is not a problem in Linux itself; it's a problem in the manufacturers who naturally want to take care of the largest market.

Best thing to do is keep emailing those who you haven't yet. Even with such a reply, enough replies from enough different people could at some point have them consider support, and if not, perhaps your device might be supported in one to several months thanks to free software devs (or perhaps it's already supported partially using a more generic driver, this mostly counts for printers though).

---

### Post by ean5533 on 2009-12-16
> **Nonsense said:**
> LINUX NEEDS TO SUPPORT MORE HARDWARE!
This needs to be top priority
Hardware is always one of the Linux kernel devs' top priorities, but believe me it's not an easy task. Even ignoring the fact that writing hardware drivers is complex and often requires a lot of reverse engineering, there are literally hundreds of thousands of hardware devices, many of which all need their own independent driver. It's not as simple as writing "a Canon scanner driver", and then all Canon scanners are covered.

Also, as someone else mentioned, the Ubuntu forums really aren't the right place to request driver development. We'd love to help, but it's just not what we do. I hate to just pass you off to someone else, but there's not much we can do about it. Like another poster above said, the manufacturer is the first person who's responsible for writing drivers. After that, it just comes down to whether or not we have driver hackers that can write one. 

Unfortunately, writing drivers isn't usually much fun, so it's hard to convince people to help out.

---

### Post by Nonsense on 2009-12-16
> **DaVince21 said:**
> While you might have been growing tired of this, hardware support in Linux is only ever increasing, and actually supports a lot more hardware than, say, Windows Vista simply because drivers only have to be written once (properly) to work forever.

The problem is where either one of the following types of hardware isn't much supported:
- Very new hardware (it's preferably up to the manufacturers, or else open-source developers, to make drivers);
- Legacy hardware that might not have been used too much in the past (fat chance on still getting drivers for that, though if the model is generic enough it might automatically gain support at some point).

Thing is, most companies don't actually focus on Linux drivers because of its tiny market share. This is not a problem in Linux itself; it's a problem in the manufacturers who naturally want to take care of the largest market.

Best thing to do is keep emailing those who you haven't yet. Even with such a reply, enough replies from enough different people could at some point have them consider support, and if not, perhaps your device might be supported in one to several months thanks to free software devs (or perhaps it's already supported partially using a more generic driver, this mostly counts for printers though).

I understand that very new or legacy hardware is hard to get driver support for, but none of the above mentioned are that old or new. And what is most ironic, they all work flawlessly in Vista. Now, I am NOT fond of Windows Vista, but this keeps me from dropping Vista altogether. For the moment I have to reboot and login to Vista if I: Want to use my webcam, want to scan a document, want to listen to music, want to copy images from my camera (without removing the memory card from the camera). I do understand there are substitutes, but I can't just keep buying new things to replace fully functioning hardware, that is all wrong in my mind. 
What really got me put off was that I just bought 3 Microsoft LifeCams for Christmas (after consulting [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) ) and now all I can do is use them as paperweights unless I want to use Windows.

---

### Post by Nonsense on 2009-12-16
> **ean5533 said:**
> Hardware is always one of the Linux kernel devs' top priorities, but believe me it's not an easy task. Even ignoring the fact that writing hardware drivers is complex and often requires a lot of reverse engineering, there are literally hundreds of thousands of hardware devices, many of which all need their own independent driver. It's not as simple as writing "a Canon scanner driver", and then all Canon scanners are covered.

Also, as someone else mentioned, the Ubuntu forums really aren't the right place to request driver development. We'd love to help, but it's just not what we do. I hate to just pass you off to someone else, but there's not much we can do about it. Like another poster above said, the manufacturer is the first person who's responsible for writing drivers. After that, it just comes down to whether or not we have driver hackers that can write one. 

Unfortunately, writing drivers isn't usually much fun, so it's hard to convince people to help out.

I'm not actually asking anyone on the forum to write me a driver, I just wanted to send a heads up. I guess this was not the right place to do it, but I couldn't think of anywhere else.

---

### Post by ean5533 on 2009-12-16
> **Nonsense said:**
> I understand that very new or legacy hardware is hard to get driver support for, but none of the above mentioned are that old or new. And what is most ironic, they all work flawlessly in Vista. Now, I am NOT fond of Windows Vista, but this keeps me from dropping Vista altogether. For the moment I have to reboot and login to Vista if I: Want to use my webcam, want to scan a document, want to listen to music, want to copy images from my camera (without removing the memory card from the camera). I do understand there are substitutes, but I can't just keep buying new things to replace fully functioning hardware, that is all wrong in my mind. 
What really got me put off was that I just bought 3 Microsoft LifeCams for Christmas (after consulting [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) ) and now all I can do is use them as paperweights unless I want to use Windows.
That's a bad situation to be in, no doubt. And, obviously, just going and buying new hardware isn't a reasonable solution. Unfortunately, I just don't think there's anything we can do to help. If the drivers don't exist, and the manufacturer refuses to create them, you have to wait until the drivers are written by someone else... for free, in their spare time.

Personally, being a huge Linux fan, I make it a point to only buy hardware that supports Linux -- I'm voting with my dollars. If enough people did the same, manufacturers would have no choice but to write their own Linux drivers, and then we'd all be much happier.

---

### Post by ean5533 on 2009-12-16
> **Nonsense said:**
> I'm not actually asking anyone on the forum to write me a driver, I just wanted to send a heads up. I guess this was not the right place to do it, but I couldn't think of anywhere else.

I honestly don't know what the "right" place is to ask. Maybe someone else can answer that question?

---

### Post by DaVince21 on 2009-12-16
Filing a bug/feature request or upvoting one that's already there on one of the major Linux driver development sites should help, but one'd have to find these places and take a bit of care not to annoy any devs there about things they already know.

Guess there really isn't a place to "vent" about this sort of stuff, though it can sprout interesting discussion (and sometimes flamewars if not carefully formulated).

---

### Post by Brian Vaughan on 2009-12-16
In the past, at least, my experience has been that Windows is better at supporting the latest hardware, but it often drops support for older (but otherwise viable) hardware. With Linux, the older the hardware, the more likely it is that there are drivers available for it. The situation has improved on both ends over time, as I think Microsoft has become less trigger-happy about dropping support for older hardware, and manufacturers have gradually been getting better about supporting Linux or at least opening the source for their drivers.

Linux has a strong hold on embedded systems, on servers, and on high-end supercomputing. It's desktop personal computing where Linux is having the hardest time making inroads. So, there's more of a push and a pull to develop drivers for NICs, hard-drives, and other critical devices for servers and the like, and less for the latest consumer-oriented video cards and gadgets. (It's worth mentioning that Microsoft is notorious for putting pressure on hardware manufacturers to favor Microsoft.)

Emailing manufacturers to ask for Linux drivers probably helps. It's unlikely to get an immediate result, but it's evidence that there's a consumer demand for Linux support.

The more user-friendly Linux distributions, like Ubuntu and Fedora, are great for even inexperienced users with older hardware -- a very large proportion of computer users -- and will run better on older hardware than the proprietary operating systems. If you're a more technically savvy user who enjoys tinkering with software, and can put up with some minor inconveniences while "hot-rodding" your computer, then Linux is your best choice. But much as I favor free software, I do have to say that if your priorities are convenience and support for the latest consumer-oriented hardware, you're probably going to be happier with the latest version of Windows.

---

### Post by salemboot on 2009-12-18
It's always been that way.  It's hard to write a driver for the type of rapid change that is the LINUX KERNEL.....  

:guitar:

Kernel developers are arrogant.  Distribution maintainers are hypocritical.  And users are relentless in finding a happy medium.

Not to put you off, but when you install Linux you accept the fact that you may never see your webcam work.  Laptops are the worst.  

Function keys, webcams, frequency scaling, power downs, ...

But at the end of the day, Microsoft isn't telling you need to register your copy of Ubuntu.  Nor is the software flagging 'trial version' all over your applications.  Mp3's play, DVD's entertain and Grandpa can safely look at his girly movies without fear of a virus interfering with his online banking.

---

